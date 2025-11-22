pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Get code from the repo configured in the job
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Static site – nothing to build.'
            }
        }

        stage('Deploy') {
            steps {
                // Windows commands using 'bat' instead of 'sh'
                bat '''
                    echo Deploying portfolio...

                    rem === destination folder for the website ===
                    set DEST=C:\\portfolio-deploy

                    rem create folder if it does not exist
                    if not exist "%DEST%" mkdir "%DEST%"

                    rem optional: clear old files
                    del /Q "%DEST%\\*" 2>nul

                    rem copy all files from workspace to DEST
                    xcopy "%WORKSPACE%\\*" "%DEST%\\" /E /I /Y

                    echo Deployment finished to %DEST%
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
