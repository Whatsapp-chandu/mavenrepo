pipeline {

  agent {
    label 'jenkins-agents'
  }

  triggers {
    pollSCM '* * * * * '
  }

  stages {

    stage ('scm-checkout') {
      steps {
        checkout scmGit(branches: [[name: '*/feat01']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-creds-chandu', url: 'https://github.com/Whatsapp-chandu/mavenrepo.git']])
        sh ' echo "my first pipeline in $BRANCH_NAME" '
       }
      }    //scm stage completes here
  
      stage ('mvn build') {
        steps {
           sh ' mvn package '
        }
      }    //buils stage completes here

      stage ('code quality') {
        steps {
           withSonarQubeEnv(credentialsId: 'sonar-jenkins-tokens',installationName: 'sonar-server') {
    // some block
           sh ' mvn sonar:sonar '
            }
        }
      }    //sonar stage completes here

      stage ('upload artifact') {
        steps {
           sh ' mvn deploy '
        }
      }    //aritifact upload stage completes here

      stage ('deploy artifact') {
        steps {
           sh ' scp /root/workspace/whatsapp/chaatting/build/sample-dev/target/studentapp-2.1.1-FEAT01-SNAPSHOT.war root@172.31.6.35:/opt/apache-tomcat-10.0.23/webapps '
        }
      }    //aritifact upload stage completes here    



  }   //all stages completed here
}    //pipeline completes here
