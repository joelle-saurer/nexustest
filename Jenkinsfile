pipeline {
    
    agent any
 
    environment {
    PATH = "/opt/Maven/apache-maven-3.6.3/bin:$PATH"
    }

 
    stages {
         
       
        stage('Deploy') {
         steps {
          echo 'Deploy the Application'
          sh 'mvn clean deploy' 
         }
        }
         
    }
}
