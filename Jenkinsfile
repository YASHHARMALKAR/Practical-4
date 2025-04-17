pipeline {
    agent any

    stages {
        stage('Confirm Checkout') {
            steps {
                echo "Code was successfully checked out by Jenkins."
                bat 'dir' // Windows equivalent of 'ls -la'
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
                // Start Node.js app in background
                bat 'start /b cmd /c "node app.js > output.log 2>&1"'
                // Show last 10 lines of the log file
                bat 'powershell -Command "Get-Content output.log -Tail 10"'
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
