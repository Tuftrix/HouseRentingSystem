pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
              echo 'Restore dependencies'
              bet  'dotnet restore'
            }
        }
        stage('Build Project') {
            steps {
              echo 'Building project'
              bat  'dotnet build --configuration Release'
            }
        }

        stage('Run dotnet test') {
            steps {
                echo 'Running tests'
                bat 'dotnet test --logger "trx;LogFileName=test_results.trx" --results-directory ./TestResults'
            }
        }
    }

    post {
        success {
            echo 'Build and tests ran successfully!'
        }
        failure {
            echo 'Something went wrong! Check logs.'
        }
    }
}
