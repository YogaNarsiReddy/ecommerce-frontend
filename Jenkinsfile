pipeline {
    agent any

    tools {
        nodejs "node js"   // Configure in Jenkins -> Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/YogaNarsiReddy/ecommerce-frontend.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'dist/**', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Frontend build completed successfully!'
        }
        failure {
            echo '❌ Frontend build failed!'
        }
    }
}
