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
                sh 'dotnet build'
            }
        }
        stage('Test') {
            steps {
                sh 'dotnet test'
            }
        }
        stage('Static Code Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'dotnet sonarscanner begin /k:"your-project-key" /d:sonar.login="your-sonar-token" /d:sonar.host.url="http://your-sonar-url"'
                    sh 'dotnet build'
                    sh 'dotnet sonarscanner end /d:sonar.login="your-sonar-token"'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh 'dotnet publish -c Release -o ./publish'
            }
        }
        stage('Deploy to Dev') {
            steps {
                sh 'echo Deploying to Dev'
            }
        }
        stage('Deploy to QAT') {
            steps {
                sh 'echo Deploying to QAT'
            }
        }
        stage('Deploy to Staging') {
            steps {
                sh 'echo Deploying to Staging'
            }
        }
        stage('Deploy to Production') {
            steps {
                sh 'echo Deploying to Production'
            }
        }
    }
}
