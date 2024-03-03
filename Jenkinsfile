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
      stage('build docker image') { 
            steps {
                sh 'sudo docker ps'
                sh 'sudo docker images'
            }
        }
    }
}
