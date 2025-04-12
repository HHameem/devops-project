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
                withSonarQubeEnv('SonarQube') {
                    bat 'dotnet sonarscanner begin /k:"your-project-key" /d:sonar.login="your-sonar-token" /d:sonar.host.url="http://your-sonar-url"'
                    bat 'dotnet build'
                    bat 'dotnet sonarscanner end /d:sonar.login="your-sonar-token"'
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
