pipeline {
  agent any

  environment {
    TOMCAT_URL = "http://localhost:8080"
    TOMCAT_USER = "admin"
    TOMCAT_PASS = "kwame912"
    APP_NAME = "my-react-app"
  }

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/richmondamponsah/react-calculator.git', branch: 'main'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy to Tomcat') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'tomcat-credentials', usernameVariable: 'TOMCAT_USER', passwordVariable: 'TOMCAT_PASS')]) {
          sh "curl --upload-file build/${APP_NAME}.war ${TOMCAT_USER}:${TOMCAT_PASS}@${TOMCAT_URL}/manager/text/deploy?path=/${APP_NAME}&update=true"
        }
      }
    }
  }
}

