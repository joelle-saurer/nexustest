pipeline {
    
    agent any
 
    tools {
        maven "Maven"
    }
    
    parameters {
      choice (
          name: 'BuildType',
          choices:"SNAPSHOT\nRELEASE",
          description: "Choose the Build type"
      )
    }
    
    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "http://192.168.1.149:8082"
        NEXUS_REPOSITORY = "testApp"
        NEXUS_CREDENTIAL_ID = "nexus-credentials"
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
          when {
            expression { params.BuildType == 'SNAPSHOT' }
          }
            
         steps {
          echo 'Deploy the Application'
          sh 'mvn -Drevision=${ARTIFACT_VERSION} deploy' 
         }
        }
        
        stage('Release') {
          when {
            expression { params.BuildType == 'RELEASE' }
          }
            
          steps {
              echo 'Release Application'
              sh 'mvn -Drevision=${ARTIFACT_VERSION} release:clean release:prepare release:perform'
         
          }
        }

    
    }   
}
