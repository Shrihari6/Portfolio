// Jenkinsfile

pipeline {
    agent any 

    stages {
        // CI: Checks out the code from the Git repository
        stage('Checkout Source Code') {
            steps {
                echo 'Checking out the latest code from GitHub.'
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
            // Defines the deployment path for Windows
                def DEPLOY_PATH_TARGET = 'C:\\jenkins_target' // Uses backslashes for Windows path
            steps {
                

                echo "Starting Windows deployment to destination: ${DEPLOY_PATH_TARGET}"

                // --- Deployment Commands ---
                
                // 1. Create directory using the Windows 'bat' step
                // The '|| exit 0' ensures the pipeline doesn't stop if the directory already exists.
                bat "mkdir %DEPLOY_PATH_TARGET% || exit 0"
                
                // 2. Copy files using xcopy (Windows equivalent of cp -r)
                // . is the current directory (Jenkins workspace)
                // /s /e /y ensure copying subdirectories, empty directories, and overwriting existing files.
                bat "xcopy /s /e /y . %DEPLOY_PATH_TARGET%" 

                echo "Deployment complete. Website files are now in ${DEPLOY_PATH_TARGET}"
            }
        }
    }

    post {
        always {
            echo 'CI/CD Pipeline finished!'
        }
    }
}
