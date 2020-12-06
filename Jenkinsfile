pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh "wget --user=admin --password=admin123 'http://repository.sonatype.org/service/local/artifact/maven/content?r=onlineCinema-SNAP&g=joelleTraineeship&a=cinema&v=LATEST' cinematest.war"
         }
        }

        
        stage('Deploy to Nexus') {
            steps{
              echo 'Upload artifact to Nexus'
              sh 'curl -v -u admin:admin123 -X POST "http://localhost:8082/service/rest/v1/components?repository=onlineCinema-REL" -F "maven2.groupId=joelleTraineeship" -F "maven2.artifactId=cinema" -F "maven2.version=3.0.0" -F "maven2.asset1=@/var/lib/jenkins/workspace/mir/cinematest.war" -F "maven2.asset1.extension=war"'
            }
        }     
     
    }
}
