// Jenkinsfile (Declarative Pipeline)

pipeline {
    agent any 

    environment {
        // NOTE: Replace the value below with the ACTUAL deployment path on your Jenkins machine.
        // Example for Linux: '/var/www/html/portfolio-live'
        // Example for Windows: 'C:\\inetpub\\wwwroot\\portfolio-live'
        DEPLOY_PATH = "<YOUR_DEPLOYMENT_PATH>" 
    }

    stages {
        // CI: Checks out the code from the Git repository
        stage('Checkout Source Code') {
            steps {
                echo 'Checking out the latest code from Git...'
                // The Pipeline job automatically handles this when "Pipeline script from SCM" is configured.
            }
        }

        // CI: Placeholder for checks
        stage('Test/Linter') {
            steps {
                echo 'Skipping formal tests, but this is where you run linting/checks.'
            }
        }

        // CD: Deploys the files to the web server directory
        stage('Deployment') {
            steps {
                echo "Starting deployment to ${DEPLOY_PATH}"

                // --- Deployment Commands (Linux/macOS Shell) ---
                // NOTE: If your Jenkins is on Windows, these commands will need to be PowerShell/Batch (e.g., 'bat "mkdir %DEPLOY_PATH%"' and 'bat "xcopy /s /e /y ." "%DEPLOY_PATH%"')
                sh "mkdir -p ${DEPLOY_PATH}"
                sh "cp -r * ${DEPLOY_PATH}"

                echo "Deployment complete. Website files are at ${DEPLOY_PATH}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}
