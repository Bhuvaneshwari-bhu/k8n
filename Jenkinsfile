pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/Bhuvaneshwari-bhu/k8n.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t k8n:${BUILD_NUMBER} .
                docker tag k8n:${BUILD_NUMBER} Bhuvaneshwari-bhu/k8n:${BUILD_NUMBER}
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push Bhuvaneshwari-bhu/k8n:${BUILD_NUMBER}'
            }
        }
        stage('Run Docker Image') {
            steps {
                sh 'docker run Bhuvaneshwari-bhu/k8n:${BUILD_NUMBER}'
            }
        }
    }
}
