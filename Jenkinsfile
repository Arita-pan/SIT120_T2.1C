pipeline {
    agent any

    tools {
        nodejs "NodeJS"
    }

    environment {
        DATADOG_API_KEY = credentials('datadog-api-key')
        RECIPIENT = 'pansuang.12@gmail.com'
    }

    stages {
        stage('Clone repository') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    app = docker.build("myexpressapp:latest")
                }
            }
        }

        
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
            emailext(
                subject: "Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """<html><body>
                        <p>GOOD NEWS!</p>
                        <p>The build was successful.</p>
                        <p>Check it out here: <a href='${BUILD_URL}'>${BUILD_URL}</a></p>
                        </body></html>""",
                mimeType: 'text/html',
                to: "${env.RECIPIENT}",
                attachLog: true
            )
        }
        failure {
            echo 'Pipeline failed.'
            emailext(
                subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """<html><body>
                        <p>ALERT!</p>
                        <p>The build has failed.</p>
                        <p>Check it out here: <a href='${BUILD_URL}'>${BUILD_URL}</a></p>
                        </body></html>""",
                mimeType: 'text/html',
                attachLog: true
            )
        }
    }
}
