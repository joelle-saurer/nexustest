 
pipeline {
    
    agent any

    node{
        stage('Checkout SCM') {
            git 'https://github.com/joelle-saurer/DevOps-Challenges.git'
        }    
        
        stage('Compile') {
            sh 'mvn compile' 
        }
        
        stage('Test') {
            sh 'mvn test'
        }
        stage('Package') {
            sh 'mvn package'
        }
    }
}

