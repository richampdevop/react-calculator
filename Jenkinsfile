pipeline {
    agent any
    
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
                withCredentials([usernamePassword(credentialsId: 'tomcat-credentials', usernameVariable: 'TOMCAT_USERNAME', passwordVariable: 'TOMCAT_PASSWORD')]) {
                    sh "curl --upload-file ./build/*.war http://localhost:8080/manager/text/deploy?path=/your-app&update=true -u ${TOMCAT_USERNAME}:${TOMCAT_PASSWORD}"
                }
            }
        }
    }
}

