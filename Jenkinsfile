pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        echo 'Cloning repo'
        git(url: 'https://github.com/DVSR1411/onlinebookstore-v2', branch: 'master')
        echo 'Repo cloned'
      }
    }

    stage('Maven') {
      steps {
        sh 'mvn clean install package'
      }
    }

    stage('Nexus') {
      steps {
        nexusArtifactUploader(nexusVersion: '2', protocol: '3', nexusUrl: '4', groupId: '5', version: '6', repository: '7', credentialsId: '8')
      }
    }

    stage('Dockerise') {
      steps {
        sh 'docker build -t .'
      }
    }

  }
}
