pipeline {
    agent any
    
    // This part ensures Jenkins finds your Java installation
    tools {
        jdk 'Java25' // Use the exact name you gave it in Step 1
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build & Test') {
            steps {
                // We use bat for Windows. gradlew will now find Java.
                bat 'gradlew clean build'
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