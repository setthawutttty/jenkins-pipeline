pipeline {
    agent any

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
            discordSend(
                description: """
✅ Build SUCCESS
Branch: ${env.BRANCH_NAME}
Build Number: #${env.BUILD_NUMBER}
Triggered by: ${currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')[0]?.userName ?: 'unknown'}
Time: ${new Date().format("yyyy-MM-dd HH:mm:ss")}
""",
                webhookURL: "https://discord.com/api/webhooks/1447481613964415126/GqWrwspWTne391BmUZXNg0wdtgXGPDoPOdrgpiBt9erHpZhbNmEyOrjNg16kZ6q62ImC:wq"
            )
        }
        failure {
            discordSend(
                description: """
❌ Build FAILED
Branch: ${env.BRANCH_NAME}
Build Number: #${env.BUILD_NUMBER}
Triggered by: ${currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')[0]?.userName ?: 'unknown'}
Time: ${new Date().format("yyyy-MM-dd HH:mm:ss")}
""",
                webhookURL: "https://discord.com/api/webhooks/1447481613964415126/GqWrwspWTne391BmUZXNg0wdtgXGPDoPOdrgpiBt9erHpZhbNmEyOrjNg16kZ6q62ImC"
            )
        }
    }
}

