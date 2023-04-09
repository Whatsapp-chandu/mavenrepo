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
        sh ' echo "my first pipeline" '
       }

      }
  
      stage ('mvn build') {
        steps {
           sh ' mvn package '
        }

      }        



  }   //all stages completed here
}    //pipeline completes here
