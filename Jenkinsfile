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
                docker build -t my-k8s-app:${BUILD_NUMBER} .
                docker tag my-k8s-app:${BUILD_NUMBER} Bhuvaneshwari-bhu/k8n:${BUILD_NUMBER}
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push Bhuvaneshwari-bhu/k8n:${BUILD_NUMBER}'
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker run Bhuvaneshwari-bhu/k8n:${BUILD_NUMBER}'
            }
        }
    }
}