 
pipeline {
    
    agent any
 
    environment {
    PATH = "/opt/Maven/apache-maven-3.6.3/bin:$PATH"
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

