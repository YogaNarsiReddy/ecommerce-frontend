pipeline {
    agent any

    tools {
        nodejs "NodeJS_18"   // Configure in Jenkins -> Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/YogaNarsiReddy/ecommerce-frontend.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
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
