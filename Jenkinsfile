pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'curl --user admin:admin123 -o petclinic.war "http://192.168.122.1:8082/service/rest/v1/search/assets/download?repository=pet-SNAP&group=devOpsTraineeship&name=petclinic&sort=version&direction=desc"' 
         }
        }

  
        stage('Deploy to Nexus') {
            steps{
              echo 'Upload artifact to Nexus'
              sh 'curl -v -u admin:admin123 POST -T petclinic.war "http://192.168.122.1:8082/service/rest/v1/components?repository=pet-REL" -F "maven2.groupId=devOpsTraineeship" -F "maven2.artifactId=petclinic" -F "maven2.version=1.0.0" -F "maven2.asset1=@/var/lib/jenkins/workspace/petDeploy/petclinic.war" -F "maven2.asset1.extension=war"'
            }
        }          
    }
}
