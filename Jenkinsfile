pipeline {
    agent any

    stages {
        stage('Checkout the repository') {
            steps {
            //Checkout code from Github and specify branch
            //git branch: 'main', url: 'https://github.com/VelVelikov/05-SeleniumIDE'
            checkout scm
            }
        }

        stage('Restore the project') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build the project') {
            steps {
                sh 'dotnet build'
            }
        }

        stage('Run tests') {
            steps {
                sh 'dotnet test'
            }
        }
    }

    post {
        success {
            echo 'Build and test succeeded!'
        }
        failure {
            echo 'Build or test failed.'
        }
    }
}