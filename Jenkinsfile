pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // 'scm' means Jenkins will use the repo configured in the job
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Static site – nothing to build. You can add linters here.'
                // Example: run HTML/CSS linters, if installed
                // sh 'npm install'
                // sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Adjust this path to your web server root
                sh '''
                    echo "Deploying portfolio to /var/www/html/portfolio"
                    mkdir -p /var/www/html/portfolio
                    cp -r * /var/www/html/portfolio
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
