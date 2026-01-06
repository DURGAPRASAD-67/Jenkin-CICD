pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/DURGAPRASAD-67/Jenkin-CICD.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker rmi -f ogranic || true
                  docker build -t organic .
                '''
            }
        }

        stage('Deploy Docker Container') {
            steps {
                sh '''
                  docker stop webapp || true
                  docker rm webapp || true

                  docker run -d \
                    --name webapp \
                    -p 8081:8080 \
                    organic
                '''
            }
        }
    }
}
