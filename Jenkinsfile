pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/princebhanderi/jenkins-pipeline-demo.git'
            }
        }

        stage('Check Python') {
            steps {
                bat 'python --version'
                bat 'pip --version'
            }
        }

        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'pytest --junitxml=report.xml'
            }
        }
    }

    post {
        always {
            junit '**/report.xml'
        }
    }
}
