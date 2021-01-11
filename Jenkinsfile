pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'curl --user admin:admin123 -o petclinic.war "http://40.114.35.24:8081/service/rest/v1/search/assets/download?repository=petclnic-SNAP&group=devOpsTraineeship&name=petclinic&sort=version&direction=desc"' 
         }
        }

  
        stage('Deploy to Nexus') {
            steps{
              echo 'Upload artifact to Nexus'
              sh 'curl -v -u admin:admin123 POST -T petclinic.war "http://40.114.35.24:8081/service/rest/v1/components?repository=petclinic-REL" -F "maven2.groupId=devOpsTraineeship" -F "maven2.artifactId=petclinic" -F "maven2.version=1.0.0" -F "maven2.asset1=@/var/lib/jenkins/workspace/Petclinic_release/petclinic.war" -F "maven2.asset1.extension=war"'
            }
        }          
    }
}
