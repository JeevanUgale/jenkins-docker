pipeline {
    agent {
        label "slave"
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
      stage('docker login') { 
            steps {
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
                sh 'docker iamges'
            }
        }
    }
}
