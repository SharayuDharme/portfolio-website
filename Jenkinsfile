pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/SharayuDharme/portfolio-website.git'
      }
    }

    stage('Build') {
      steps {
        echo "Static site - no build required"
      }
    }

    stage('Deploy to webroot') {
      steps {
        bat '''
          echo Deploying to webroot...
          if not exist "C:\\inetpub\\wwwroot\\" mkdir "C:\\inetpub\\wwwroot\\"
          xcopy /E /Y /I "%WORKSPACE%\\*" "C:\\inetpub\\wwwroot\\"
        '''
      }
    }
  }

  post {
    success { echo "Deployment finished." }
    failure { echo "Deployment failed." }
  }
}
