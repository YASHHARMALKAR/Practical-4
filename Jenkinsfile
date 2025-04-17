pipeline {
    agent any

    environment {
        // Change the repo URL to your actual GitHub repo
        REPO_URL = 'https://github.com/YASHHARMALKAR/Practical-4.git'
        APP_DIR = 'nodejs-app'
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning Node.js app from GitHub..."
                git url: "${REPO_URL}"
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing npm dependencies..."
                sh 'npm install'
            }
        }

        stage('Deploy Application') {
            steps {
                echo "Starting the Node.js server..."
                // This assumes app entry point is app.js or index.js
                sh 'nohup node app.js > output.log 2>&1 &'
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
