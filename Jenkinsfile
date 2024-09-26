pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository with the HTML file
                git 'https://github.com/Arita-pan/LearnTrack.git'
            }
        }

        stage('Test HTML') {
            steps {
                // Run HTML validation (optional)
                sh 'htmlhint index.html'
            }
        }

        stage('Deploy') {
            steps {
                // Example deployment to GitHub Pages
                // Ensure your repository is set to deploy from the correct branch
                sh 'git push origin main'
            }
        }

        stage('Monitoring') {
            steps {
                // Optional: Monitor website performance using Google Lighthouse
                //sh 'lighthouse http://yourwebsite.com --output=json'
            }
        }
    }
}
