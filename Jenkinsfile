pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone your GitHub repository
                git 'https://github.com/princebhanderi/jenkins-pipeline-demo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                // Install Python dependencies
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Run pytest and generate JUnit XML report
                sh 'pytest --junitxml=report.xml'
            }
        }
    }

    post {
        always {
            // Publish test results
            junit 'report.xml'
        }
    }
}
