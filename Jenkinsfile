pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'curl --user admin:admin123 -o onlinecinemat.war http://localhost:8082/repository/onlineCinema-SNAP/joelleTraineeship/cinema/1.1.0-SNAPSHOT/cinema-1.1.0-20201206.165940-2.war' 
         }
        }

  
        stage('Deploy to Nexus') {
            steps{
              echo 'Upload artifact to Nexus'
              sh 'curl -v -u admin:admin123 POST -T onlinecinemat.war "http://localhost:8082/service/rest/v1/components?repository=onlineCinema-REL" -F "maven2.groupId=joelleTraineeship" -F "maven2.artifactId=cinemat" -F "maven2.version=1.2.0" -F "maven2.asset1=@/var/lib/jenkins/workspace/nexusDeploy/onlinecinema.war" -F "maven2.asset1.extension=war"'
            }
        }          
    }
}
