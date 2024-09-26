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
                    // Build the Vue.js project
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    
                        // Run the Vue.js unit tests
                        sh 'npm run test:unit'
                    
                    }
                }
            }
        }
    }
        

    

