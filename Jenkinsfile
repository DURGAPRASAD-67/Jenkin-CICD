pipeline {
    agent any
 
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/DURGAPRASAD-67/Jenkin-CICD.git'
            }
        }
        stage('mvn Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Docker Image') {
            steps {
                sh 'docker build -t amazon .'
            }
        }
        stage('Docker Deploy') {
            steps {
                sh 'docker run -d -p 6060:8080 --name azure amazon'
            }
        }
    }
