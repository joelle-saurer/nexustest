pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'wget --user=admin --password=admin123 http://localhost:8082/repository/onlineCinema-SNAP/joelleTraineeship/cinema/1.0.0-SNAPSHOT/cinema-1.0.0-20201204.093819-1.war'
         }
        }

        stage('Rename') {
         steps {
          echo 'Rename artifact'
          sh 'mv cinema-1.0.0-20201204.093819-1.war onlinecinemafile.war'
         }
        }
        
        stage('Deploy to Nexus') {
            steps{
              echo 'Upload artifact to Nexus'
              sh 'cd /var/lib/jenkins/workspace/mir/'
              sh 'curl -v -u admin:admin123 --upload-file onlinecinemafile.war http://localhost:8082/repository/onlineCinema-REL/'
               

            }
        }
     
  
    }   
}
