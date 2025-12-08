pipeline {
    agent any
    stages {
        stage('Build and Test') {
            steps {
                echo "Building and testing on branch: ${env.BRANCH_NAME}"
                // ใส่คำสั่ง Build และ Test ของคุณที่นี่
                sh 'echo "Simulating: npm install && npm test"'
            }
        }

        // Stage นี้จะทำงานเสมอ เพราะเรามั่นใจว่ามันคือ branch main แล้ว
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production Server...'
                sh 'echo "Simulating: Deploying to production environment"'
            }
        }
    }

    post {
        always {
            echo "Pipeline for branch ${env.BRANCH_NAME} finished."
        }
        success {
            echo "SUCCESS: Deployed to production successfully."
        }
        failure {
            echo "FAILURE: Pipeline failed. Check logs for errors."
        }
    }
}
