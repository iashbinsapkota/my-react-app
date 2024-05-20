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
                bat 'npm test -- --coverage --reporters=default --reporters=jest-junit' // Run automated tests with coverage and JUnit reporting
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
