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
        echo 'Deploying all files to IIS folder'
        bat """
            if not exist "${DEPLOY_DIR}" mkdir "${DEPLOY_DIR}"
            xcopy /Y /E /I Home.html "${DEPLOY_DIR}\\"
            xcopy /Y /E /I about.html "${DEPLOY_DIR}\\" 2>nul
            xcopy /Y /E /I style.css "${DEPLOY_DIR}\\" 2>nul
        """
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
            echo 'Pipeline finished successfully! Visit: http://localhost:8080/protfolio'
        }
        failure {
            echo 'Pipeline failed! Check build logs.'
        }
    }
}
