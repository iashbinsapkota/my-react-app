pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        script {
          // Get latest code from Git repository (assuming credentials are configured)
          git branch: 'main', url: 'https://github.com/iashbinsapkota/floodshield.git'
        }
      }
    }
    stage('Build React App') {
      steps {
        bat 'npm install'// Install dependencies
        bat 'npm start' // Build the React app
        bat 'npm install jest-junit --save-dev'
      }
    }
    stage('Test') {
            steps {
                bat 'npm test -- --passWithNoTests' // Run automated tests with coverage and JUnit reporting
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/**', allowEmptyArchive: true // Archive the build artifacts
            junit 'coverage/junit/*.xml' // Archive the test results
        }
    }
}
