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

    post {
        success {
            // ส่ง notification เมื่อ build สำเร็จ
            discordSend(
                description: "Build SUCCESS on branch ${env.BRANCH_NAME}",
                webhookURL: "https://discord.com/api/webhooks/1447481613964415126/GqWrwspWTne391BmUZXNg0wdtgXGPDoPOdrgpiBt9erHpZhbNmEyOrjNg16kZ6q62ImC"
            )
        }
        failure {
            // ส่ง notification เมื่อ build fail
            discordSend(
                description: "Build FAILED on branch ${env.BRANCH_NAME}",
                webhookURL: "https://discord.com/api/webhooks/1447481613964415126/GqWrwspWTne391BmUZXNg0wdtgXGPDoPOdrgpiBt9erHpZhbNmEyOrjNg16kZ6q62ImC"
            )
        }
    }
}

