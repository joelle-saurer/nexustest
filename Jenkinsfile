 
pipeline {
    
    agent any
 
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
           sh 'mvn package'
         }
        }
    }
}

