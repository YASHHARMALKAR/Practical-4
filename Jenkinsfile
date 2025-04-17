pipeline {
    agent any

    stages {
        stage('Confirm Checkout') {
            steps {
                echo "Code was successfully checked out by Jenkins."
                sh 'ls -la'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing npm dependencies..."
                bat 'npm install'
            }
        }

        stage('Deploy Application') {
            steps {
                echo "Starting the Node.js server..."
                bat 'start /b cmd /c "node index.js > output.log 2>&1"'
                powershell 'Get-Content output.log -Tail 10'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
