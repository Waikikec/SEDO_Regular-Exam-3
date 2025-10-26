pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:8.0'
            args '-v /tmp:/tmp' // optional
        }
    }

    stages {
        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build Application') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
        success {
            echo '✅ Build and tests passed successfully!'
        }
        failure {
            echo '❌ Build or tests failed. Check logs for details.'
        }
    }
}
