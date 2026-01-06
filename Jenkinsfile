pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/your-repo/project.git'
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
                  docker build -t maven-web-app:${BUILD_NUMBER} .
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
                    maven-web-app:${BUILD_NUMBER}
                '''
            }
        }
    }
}
