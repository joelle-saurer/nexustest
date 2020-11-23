 
pipeline {
    
    agent any
    environment {
    PATH = "/opt/Maven/apache-maven-3.6.3/bin:$PATH"
    }
 
    stages{
        stage('Checkout SCM') {
         steps {
          git 'https://github.com/joelle-saurer/DevOps-Challenges.git'
         } 
        }
        
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

