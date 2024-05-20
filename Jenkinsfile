pipeline {
  agent any

  stages {
    stage('Build React App') {
      steps {
        bat 'npm install'// Install dependencies
        bat 'npm run build'      // Build the React app
        bat 'npm install jest-junit --save-dev'
      }
    }
    stage('Test') {
            steps {
                bat 'npm test -- --passWithNoTests' // Run automated tests
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/**', allowEmptyArchive: true // Archive the build artifacts
            
        }
    }
}
