pipeline {
    agent any

    environment {
        APP_PORT = '9090'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository using the personal access token
                script {
                    withCredentials([string(credentialsId: 'github-token', variable: 'GITHUB_TOKEN')]) {
                        sh 'git clone https://${GITHUB_TOKEN}@github.com/VladyslavDmytruk/devopsjenkins1.git'
                        sh 'cd devopsjenkins1'
                    }
                }
            }
        }
        stage('Build') {
            steps {
                // Use the maven package phase to build the project
                sh 'mvn clean package'
            }
        }
        stage('Unit Test') {
            steps {
                // Use the maven test phase to run unit tests
                sh 'mvn test'
            }
        }
    }
}

