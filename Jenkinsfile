pipeline {
    agent any

    environment {
        NODE_HOME = tool name 'NodeJS 16', type 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
        PATH = ${NODE_HOME}bin${env.PATH}
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url 'httpsgithub.comyour-usernameyour-nodejs-repo.git', branch 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Deploy to Local Server') {
            steps {
                echo 'Deploying...'
                sh 'pkill node  true'
                sh 'nohup npm start &'
            }
        }
    }

    post {
        success {
            echo ' Deployment successful!'
        }
        failure {
            echo ' Deployment failed.'
        }
    }
}
