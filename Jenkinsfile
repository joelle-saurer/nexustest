pipeline {
    
    agent any
 
    tools {
        maven "Maven"
    }

    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "http://192.168.1.149:8082"
        NEXUS_REPOSITORY = "testApp"
        NEXUS_CREDENTIAL_ID = "nexus-credentials"
    }

 
    stages {
         
        stage('Test') {
         steps {
          echo 'Test the Application'
          sh 'mvn test'
         }
        }


        stage('Build') {
         steps {
          echo 'Build the Application'
          sh 'mvn package'
         }
        }

        stage('Deploy') {
         steps {
          echo 'Deploy the Application'
          sh 'mvn deploy'
         }
        }
   
        
        stage("Publish to Nexus") {
            steps {
                script {
                    pom = readMavenPom file: "pom.xml";
                   
                    artifactExists = fileExists artifactPath;
                    if(artifactExists) {
                        echo "*** File: ${artifactPath}, group: ${pom.groupId}, packaging: ${pom.packaging}, version ${pom.version}";
                        nexusArtifactUploader(
                            nexusVersion: NEXUS_VERSION,
                            protocol: NEXUS_PROTOCOL,
                            nexusUrl: NEXUS_URL,
                            groupId: pom.groupId,
                            version: pom.version,
                            repository: NEXUS_REPOSITORY,
                            credentialsId: NEXUS_CREDENTIAL_ID,
                            artifacts: [
                                [artifactId: pom.artifactId,
                                classifier: '',
                                file: artifactPath,
                                type: pom.packaging],
                                [artifactId: pom.artifactId,
                                classifier: '',
                                file: "pom.xml",
                                type: "pom"]
                            ]
                        );
                    } else {
                         error "*** File: ${artifactPath}, could not be found";
                    }
                }

    }   
}
