pipeline {
    agent any
    stages {
        stage('Build and Test') {
            steps {
		echo "AUTO-BUILD TEST: This is a new change to test the trigger!"
                echo "Building and testing on branch: ${env.BRANCH_NAME}"
                sh 'echo "Simulating: npm install && npm test"'
            }
        }

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
