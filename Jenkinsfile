pipeline {
    agent none
    options {
        skipStagesAfterUnstable()
    }
    stages {

     stage('Prepare') {
      
      git credentialsId: 'git-cred', url: 'https://github.com/Maram-Rebai/test.git'
      if (!fileExists("docker-compose.yml")) {
         error('Dockerfile pas trouve')
          }
       }

     stage('Build') {
         agent {
                docker {
                    image 'ubuntu:latest'
                }
            }
         steps {
                sh "docker-compose build"
               }
        
    }

    stage('Test'){
        steps {
                echo 'Testing..'
            }
    }

    stage("Run"){
        sh "docker-compose up "
    }
}