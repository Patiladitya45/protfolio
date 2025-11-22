pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot'   // IIS web root folder
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning project from GitHub...'
                git branch: 'main', url: 'https://github.com/Patiladitya45/protfolio.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Build Step: Check files in workspace'
                bat 'dir'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying Home.html to IIS folder"

                // Directly copy Home.html to webserver root
                bat "xcopy /Y Home.html ${DEPLOY_DIR}\\"
            }
        }

        stage('Run HTTP Server (Optional Test)') {
            steps {
                echo 'Skipping HTTP server (use IIS instead)'
                // For testing, you can use: bat 'python -m http.server 8000'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully! Visit: http://localhost/protfolio.git'
        }
        failure {
            echo 'Pipeline failed! Check build logs.'
        }
    }
}
