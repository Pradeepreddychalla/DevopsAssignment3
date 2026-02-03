pipeline {
    agent any
    
    // This part ensures Jenkins finds your Java installation
    tools {
        jdk 'Java25' 
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build & Test') {
            steps {
                
                bat 'gradle clean build'
            }
        }
    }
    
    post {
        success {
            // This satisfies the "Archive Artifact" requirement of Task 2
            archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
        }
    }
}