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
        stage('Deployment') {
            steps {
                script {
                    echo 'Starting deployment to Linux target...'
                    sh '''
                        echo "Deploying project..."
                        mkdir -p ~/jenkins_target
                        cp -r * ~/jenkins_target/
                        echo "Deployment complete."
                    '''
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
