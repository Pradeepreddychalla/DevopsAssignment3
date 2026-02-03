pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // This automatically checks out code from the SCM (GitHub) configured in the job
                checkout scm
            }
        }
        
        stage('Build & Test') {
            steps {
                // Run Gradle clean and build (includes tests)
                // Use 'bat' for Windows Jenkins, use 'sh' if your Jenkins is on Linux
                bat 'gradlew clean build'
            }
        }
    }
    
    post {
        success {
            // Archive the JAR file generated in build/libs
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
        }
    }
}