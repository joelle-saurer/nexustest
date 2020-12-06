pipeline {
    
    agent any
 
    stages {
         
        stage('Pull') {
         steps {
          echo 'Pull Artifact'
          sh 'wget --user=admin --password=admin123 http://repository.sonatype.org/service/local/artifact/maven/redirect?r=onlineCinema-SNAP&g=joelleTraineeship&a=cinema&v=LATEST'
         }
        }
        
     
    }
}
