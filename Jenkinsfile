pipeline {
    
    agent any
 


    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "http://192.168.1.149:8082"
        NEXUS_REPOSITORY = "testApp"
        NEXUS_CREDENTIAL_ID = "nexus-credentials"
    }

 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'wget --user=admin --password=admin http://localhost:8082/repository/onlineCinema-SNAP/joelleTraineeship/cinema/0.2.1-SNAPSHOT/cinema-0.2.1-20201203.140758-1.war'
         }
        }


        stage('Rename') {
         steps {
          echo 'Rename artifact'
          sh 'mv cinema-0.2.1-20201203.140758-1.war cinema.war'
         }
        }

        

    }   
}
