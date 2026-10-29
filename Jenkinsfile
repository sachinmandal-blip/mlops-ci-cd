pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mkdir -p dist'
                sh 'cp index.html dist/index.html'
                echo 'Build successful'
            }
        }

        stage('Test') {
            steps {
                sh 'grep -q "MLOps Demo" index.html'
                echo 'Test passed'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p deployed'
                sh 'cp dist/index.html deployed/index.html'
                echo 'Deployment successful'
            }
        }
    }

    post {
        success {
            emailext(
                to: 'sachin.mandal@somaiya.edu',
                subject: "SUCCESS: ${env.JOB_NAME}",
                body: "Build ${env.BUILD_NUMBER} completed successfully."
            )
        }
        failure {
            emailext(
                to: 'YOUR_GMAIL@gmail.com',
                subject: "FAILED: ${env.JOB_NAME}",
                body: "Build ${env.BUILD_NUMBER} failed. Check Jenkins console output."
            )
        }
    }
}
