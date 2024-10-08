pipeline {
    agent any
    tools {
        jdk "JAVA_HOME"
        maven "M2_HOME"
    }
    stages {
        stage('Git Clone') {
            steps {
                git 'https://github.com/shashirajraja/onlinebookstore.git'
            }
        }
        stage('Maven Build') {
            steps {
                sh "mvn clean install package"
            }
        }
        stage('Nexus Artifact Upload') {
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'onlinebookstore', classifier: '', file: 'target/onlinebookstore.war', type: 'war']], credentialsId: 'nexus', groupId: 'onlinebookstore', nexusUrl: '15.207.107.124:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'onlinebookstore', version: '0.0.1-SNAPSHOT'
            }
        }
        stage('Dockerise') {
          steps {
            sh 'docker build -t .'
        }
    }
  }
}
