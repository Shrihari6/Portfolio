// Jenkinsfile (Windows Deployment Pipeline - FINAL FIX)

pipeline {
    agent any 

    stages {
        stage('Checkout Source Code') {
            steps {
                echo 'Code checked out successfully from GitHub.'
            }
        }

        stage('Test/Linter') {
            steps {
                echo 'Skipping formal tests, but this is where you run linting/checks.'
            }
        }

        // CD: Deploys the files to the web server directory
        stage('Deployment') {
            steps {
                // *** FIX 1: The 'script' block must be singular ***
                script {
                    
                    // Defines the deployment path for Windows
                    def deployPath = 'C:\\jenkins_target' 
                    
                    // *** FIX 2: Use the correctly defined variable (deployPath) in the echo statement ***
                    echo "Starting Windows deployment to destination: ${deployPath}"

                    // 1. Create directory using the Windows 'bat' step
                    bat "mkdir ${deployPath} || exit 0"
                    
                    // 2. Copy files using xcopy
                    bat "xcopy /s /e /y . ${deployPath}" 

                    echo "Deployment complete. Website files are now in ${deployPath}"
                }
            }
        }
    }

    post {
        always {
            echo 'CI/CD Pipeline finished!'
        }
    }
}
