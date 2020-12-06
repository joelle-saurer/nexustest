pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'wget --user=admin --password=admin123 http://localhost:8082/repository/onlineCinema-SNAP/joelleTraineeship/cinema/1.1.0-SNAPSHOT/cinema-1.1.0-20201206.165940-2.war' 
         }
        }

        
        stage('Deploy to Nexus') {
            steps{
              echo 'Upload artifact to Nexus'
              sh 'curl -v -u admin:admin123 -X POST "http://localhost:8082/service/rest/v1/components?repository=onlineCinema-REL" -F "maven2.groupId=joelleTraineeship" -F "maven2.artifactId=cinema" -F "maven2.version=1.1.0" -F "maven2.asset1=@/var/lib/jenkins/workspace/mir/*.war" -F "maven2.asset1.extension=war"'
            }
        }     
     
    }
}
