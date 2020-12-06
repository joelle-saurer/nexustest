pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'curl --user admin:admin123 -o onlinecinema.war "http://localhost:8082/service/rest/v1/search/assets/download?repository=onlineCinema-REL&group=joelleTraineeship&name=cinema&sort=version&direction=desc"' 
         }
        }

  
        stage('Deploy to Nexus') {
            steps{
              echo 'Upload artifact to Nexus'
              sh 'curl -v -u admin:admin123 POST -T onlinecinema.war "http://localhost:8082/service/rest/v1/components?repository=onlineCinema-REL" -F "maven2.groupId=joelleTraineeship" -F "maven2.artifactId=cinema" -F "maven2.version=1.2.0" -F "maven2.asset1=@/var/lib/jenkins/workspace/nexusDeploy/onlinecinema.war" -F "maven2.asset1.extension=war"'
            }
        }          
    }
}
