pipeline {
    agent any

    stages {
        stage('Checkout code') {
            steps {
            //Checkout code from Github and specify branch
            git branch: 'main', url: 'https://github.com/VelVelikov/05-SeleniumIDE'
            }
        }

        stage('Build and test'){
            steps{
                sh 'dotnet build'
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