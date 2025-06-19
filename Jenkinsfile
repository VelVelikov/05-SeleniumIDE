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
                sh 'dotnet build --configuration Release'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test --no-build  --logger "trx;LogFileName=test_results.trx" --results-directory TestResults'
            }
        }

        stage('Publish Artifacts') {
            steps {
                sh 'dotnet publish SeleniumIDE/SeleniumIde.csproj -c Release -o publish'
                archiveArtifacts artifacts: 'publish/**', fingerprint: true
            }
        }
    }

    post {
        always {
            // Archive the raw .trx test result for inspection
            archiveArtifacts artifacts: 'TestResults/*.trx', fingerprint: true

            // Optional: If you install and use trx2junit, convert to XML and use:
            // junit 'TestResults/*.xml'

            cleanWs()
        }
    }
}