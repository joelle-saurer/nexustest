pipeline {
    
    agent any
 
    environment {
    PATH = "/opt/Maven/apache-maven-3.6.3/bin:$PATH"
    }

 
    stages {
         
        stage('Test') {
         steps {
          echo 'Test the Application'
          sh 'mvn test'
         }
        }


        stage('Build') {
         steps {
          echo 'Build the Application'
          sh 'mvn package'
         }
        }

        stage('Deploy') {
         steps {
          echo 'Deploy the Application'
          sh 'mvn clean deploy' 
         }
        }
         
    }
}
