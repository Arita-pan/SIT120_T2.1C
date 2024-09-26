pipeline {
    agent any

    tools {
        nodejs "NodeJS"
    }

    environment {
        //DATADOG_API_KEY = credentials('datadog-api-key')
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

        stage('Test') {
            steps {
                script {
                    app.inside {
                        // Run the Vue.js unit tests
                        sh """
                        cd /usr/src/app
                        npm test
                        npm run test:unit
                        """
                    }
                    
                    }
                }
            }
        }
    }
        

    

