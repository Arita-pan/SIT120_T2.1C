pipeline {
    agent any

    stages {
        // Build Stage
        stage('Build') {
            steps {
                script {
                    echo "Building the Vue.js project"
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        // Test Stage
        stage('Test') {
            steps {
                script {
                    echo "Running Tests"
                    sh 'npm run test'
                }
            }
        }

        // Deploy Stage
        stage('Deploy') {
            steps {
                script {
                    echo "Deploying to staging environment"
                    // You can use Docker, AWS, or other deployment methods
                    sh 'npm run deploy'
                }
            }
        }
    }

    // Post-actions to archive build artifacts and notify
    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
