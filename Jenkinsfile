pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/rohithbairi9/node-docker-app.git'
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
                docker build -t node-docker-app:${BUILD_NUMBER} .
                docker tag node-docker-app:${BUILD_NUMBER} rohith1729/node-docker-app:${BUILD_NUMBER}
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'echo "rgukt123" | sudo -S docker push rohith1729/node-docker-app:4'
            }
        }
        
        stage('Create container') {
            steps {
                sh 'docker run -d -p 3000:8080 rohith1729/node-docker-app:${BUILD_NUMBER}'
            }
        }



    }
}
