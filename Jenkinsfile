// Jenkinsfile (Declarative Pipeline)

pipeline {
    agent any // Run on any available Agent (Windows is required for the 'bat' step)

    stages {
        // --- Stage 1: Continuous Integration (CI) ---
        stage('Checkout Source Code') {
            steps {
                echo 'Code checked out successfully from GitHub.'
                // In a real pipeline, use 'checkout scm' here.
            }
        }

        // --- Stage 2: Quality Gate ---
        stage('Test/Linter') {
            steps {
                echo 'Skipping formal tests, but this is where you run linting/checks.'
                // sh 'npm run lint' or 'mvn test'
            }
        }

        // --- Stage 3: Continuous Deployment (CD) ---
        stage('Deployment') {
            steps {
                script { // Allows defining and using Groovy variables
                    
                    // Defines the deployment path for the Windows server
                    def deployPath = 'C:\\jenkins_target' 
                    
                    echo "Starting Windows deployment to destination: ${deployPath}"

                    // 1. Create target directory (|| exit 0 prevents failure if it exists)
                    bat "mkdir ${deployPath} || exit 0"
                    
                    // 2. Copy all files from the current workspace to the target path
                    // /s /e /y: Copy subdirectories, including empty ones, overwrite without prompt
                    bat "xcopy /s /e /y . ${deployPath}" 

                    echo "Deployment complete. Website files are now in ${deployPath}"
                }
            }
        }
    }

    post {
        always {
            echo 'CI/CD Pipeline finished!' // Final completion message
        }
    }
}
