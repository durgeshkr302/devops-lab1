pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Building the application...'
                sh 'chmod +x app.sh'
            }
        }
        stage('Test') {
            steps {
                echo 'Stage 2: Running automated verification tests...'
                sh './app.sh | grep "Application v1.0 running successfully!"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Stage 3: Deploying application to local staging environment...'
                sh 'mkdir -p /tmp/staging && cp app.sh /tmp/staging/ && /tmp/staging/app.sh'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline executed and deployed successfully!'
        }
        failure {
            echo 'CI/CD Pipeline failed. Check console logs for errors.'
        }
    }
}
