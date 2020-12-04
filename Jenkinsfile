pipeline {
    
    agent any
 
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

        nexusArtifactUploader artifacts: [
          [
             artifactId: 'cinema', 
             classifier: '', 
             file: 'cinema.war', 
             type: 'war'
          ]
        ], 
         
        credentialsId: 'nexus-credentials', 
        groupId: 'joelleTraineeship', 
        nexusUrl: '192.168.122.1:8082',
        nexusVersion: 'nexus3',
        protocol: 'http', 
        repository: 'http://localhost:8082/repository/onlineCinema-REL/', 
        version: '1.0.0'   

    }   
}
