pipeline {
    
    agent any
 
    tools {
        maven "Maven"
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
          sh 'mvn deploy'
         }
        }
      
    
    }   
}
