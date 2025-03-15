pipeline {
    agent any
    stages {
        stage('Checkout the Code from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/rajath06/Banking-java-project.git'
                echo 'GitHub repository checked out'
            }
        }
        stage('Code Compilation') {
            steps {
                echo 'Starting compilation'
                sh 'mvn compile'
            }
        }
        stage('Code Testing') {
            steps {
                sh 'mvn test'
            }
        }
        stage('QA Check') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('Package Application') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myimg .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
