pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        script {
          // Get latest code from Git repository (assuming credentials are configured)
          git branch: 'main', url: 'https://github.com/iashbinsapkota/my-react-app.git'
        }
      }
    }
    stage('Build React App') {
      steps {
        sh 'npm install'// Install dependencies
      }
    }
    stage('Start React App (Optional)') { // This stage can be removed if not needed
      steps {
        sh 'npm start' // Build the React app
      }
    }
  }
}
