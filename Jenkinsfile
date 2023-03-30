pipeline {
  agent any


  environment {
   CI = 'true'
    HOME = '.'
    npm_config_cache = 'npm-cache'
  }
  
  tools {nodejs "nodejs"}
  
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/richmondamponsah/react-calculator.git', branch: 'main'
      }
    }

    stage('install dependancy') {
      steps {
        sh 'npm install'
        sh 'export NODE_OPTIONS=--openssl-legacy-provider'
      }
    }
  stage('Create Build Artifacts') {
          steps {
            sh 'npm run build'
          }
        }
      }
    }

    
