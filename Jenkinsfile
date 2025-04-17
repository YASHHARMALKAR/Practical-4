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
                bat  'npm install'
            }
        }

        stage('Deploy Application') {
            steps {
                echo "Starting the Node.js server..."
                sh 'nohup node app.js > output.log 2>&1 &'
                sh 'tail -n 10 output.log'
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
