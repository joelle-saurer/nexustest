 
pipeline {
    
    agent any
    environment {
    PATH = "/opt/Maven/apache-maven-3.6.3/bin:$PATH"
    }
 
    stages{
        
        stage('Compile') {
         steps{
          sh 'mvn compile' 
         }
        }
         
        
        stage('Test') {
         steps{   
          sh 'mvn test'
         }
        }
     
        stage('Deploy') {
         steps{
            sh 'mvn package'
         }
        }
    }
}

