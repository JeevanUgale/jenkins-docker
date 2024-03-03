pipeline {
    agent {
        label "slave"
    }
    environment {
        SUDO_PROMPT = ''
        SUDO_ASKPASS = ''
    }
    tools {
        maven 'maven'
    }
    stages {
        
        //stage('mvn test and build') { 
         //   steps {
           //     sh 'mvn clean package'
            //}
        //}
        stage {
            steps {
                script {
                  withCredentials([usernamePassword(credentialsId: 'dockerhub-cred', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'sudo docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                  }
                }
            }
        }
      stage('build docker image') { 
            steps {
                sh 'sudo docker ps'
                sh 'sudo docker images'
            }
        }
    }
}
