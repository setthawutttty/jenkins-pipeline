pipeline {
    agent any

    options {
        skipDefaultCheckout true
    }

    stages {
        stage('Check branch') {
            when {
                branch 'main'
            }
            steps {
                echo "This is main branch, building..."
            }
        }
    }
}

