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
                title: "Jenkins Build",
                color: "GREEN"
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
                title: "Jenkins Build",
                color: "RED"
            )
        }
    }
}

