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
        sh 'cat Jenkinsfile'
      }

    }



  }   //all stages completed here
}    //pipeline completes here
