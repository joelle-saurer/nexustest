 
pipeline {
    
    agent any
    environment {
    SERVER_CREDENTIALS = credentials ('server-credentials')
    }
 
    tools {
        maven 'Maven'
    }
 
    stages {
        
        stage('Compile') {
         steps {
          echo 'Building the Application'
          sh 'mvn compile' 
         }
        }
         
        
        stage('Test') {
         steps { 
          echo 'Testing the Application'
          sh 'mvn test'
         }
        }
     
        stage('Deploy') {
         steps {
           echo 'Deploying the Application'
           echo 'Deploying with ${SERVER_CREDENTIALS}'
           sh '${SERVER_CREDENTIALS}'
           sh 'mvn package'
         }
        }
    }
}

