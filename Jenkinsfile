pipeline {
    agent any
    environment {
        SCM_URL = 'https://github.com/HHameem/devops-project.git'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: "${SCM_URL}", branch: 'main'  
            }
        }
        stage('Build') {
            steps {
                bat 'dotnet build'
            }
        }
        stage('Test') {
            steps {
                bat 'dotnet test'
            }
        }
        stage('Static Code Analysis') {
            steps {
                script {
                    def result = bat(script: 'dotnet format --verify-no-changes', returnStatus: true)
                    if (result != 0) {
                        echo "Formatting issues found, but continuing..."
                    }
                }
            }
        }
        stage('Deliver') {
            steps {
                bat 'dotnet publish -c Release -o ./publish'
            }
        }
        stage('Deploy to Dev') {
            steps {
                bat 'echo Deploying to Dev'
            }
        }
        stage('Deploy to QAT') {
            steps {
                bat 'echo Deploying to QAT'
            }
        }
        stage('Deploy to Staging') {
            steps {
                bat 'echo Deploying to Staging'
            }
        }
        stage('Deploy to Production') {
            steps {
                bat 'echo Deploying to Production'
            }
        }
    }
}
