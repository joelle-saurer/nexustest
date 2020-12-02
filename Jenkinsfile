pipeline {
    
    agent any
 
    environment {
    PATH = "/opt/Maven/apache-maven-3.6.3/bin:$PATH"
    }

 
    stages {
        
        stage('Test') {
         steps { 
          echo 'Testing the Application'
          sh 'mvn test'
         }
        }
     
        stage('Build') {
         steps {
           echo 'Package the Application'
           sh 'mvn package'
         }
        }
       
        stage('Deploy') {
         steps {
          echo 'Deploy the Application'
          sh 'mvn deploy' 
         }
        }
         
    }
}
