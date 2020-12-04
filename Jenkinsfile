pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'wget --user=admin --password=admin http://localhost:8082/repository/onlineCinema-SNAP/joelleTraineeship/cinema/1.0.0-SNAPSHOT/cinema-1.0.0-20201204.093819-1.war'
         }
        }

        stage('Rename') {
         steps {
          echo 'Rename artifact'
          sh 'mv cinema-1.0.0-20201204.093819-1.war onlinecinema.war'
         }
        }

        stage('Deploy to Nexus') {
            steps{
              
                
                nexusArtifactUploader artifacts: [
                [
                  artifactId: 'cinema', 
                  classifier: '', 
                  file: 'target/onlinecinema.war', 
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
    }   
}
