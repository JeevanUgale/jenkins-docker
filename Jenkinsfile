pipeline {
    agent {
        label "master"
    }
    environment {
        SUDO_PROMPT = ''
        SUDO_ASKPASS = ''
    }
    tools {
        maven 'maven'
    }
    stages {
        
        stage('mvn test and build') { 
            steps {
                sh 'mvn clean package'
                stash includes: '**/*.war', name: 'mywar'
            }
        }
        stage('docker login') {
            agent {
                label "slave"
            }
            steps {
                unstash 'mywar'
                script {
                  withCredentials([usernamePassword(credentialsId: 'dockerhub-cred', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                  }
                }
            }
        }
      stage('build docker image') { 
            steps {
                sh 'docker ps'
                sh 'docker images'
            }
        }
    }
}
