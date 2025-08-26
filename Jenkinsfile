pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build commands here
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add test commands here
                // Uncomment the next line to simulate a failure
                // sh 'exit 1'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add deploy commands here
            }
        }
    }

    post {
        success {
            emailext (
                subject: "✅ SUCCESS: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: """
                <p>Hello Jayanthi,</p>
                <p>The Jenkins pipeline <b>${env.JOB_NAME} [${env.BUILD_NUMBER}]</b> has <b>SUCCESSFULLY completed</b>.</p>
                <p>Check build details here: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                """,
                to: "jayanthi1200@gmail.com"
            )
        }

        unstable {
            emailext (
                subject: "⚠️ UNSTABLE: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: """
                <p>Hello Jayanthi,</p>
                <p>The Jenkins pipeline <b>${env.JOB_NAME} [${env.BUILD_NUMBER}]</b> completed with <b>UNSTABLE status</b> (e.g., some test failures).</p>
                <p>Check build details here: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                """,
                to: "jayanthi1200@gmail.com"
            )
        }

        failure {
            emailext (
                subject: "❌ FAILURE: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: """
                <p>Hello Jayanthi,</p>
                <p>The Jenkins pipeline <b>${env.JOB_NAME} [${env.BUILD_NUMBER}]</b> has <b>FAILED</b>.</p>
                <p>Check logs here: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                """,
                to: "jayanthi1200@gmail.com"
            )
        }

        always {
            echo "Pipeline finished (success, unstable, or failure)."
        }
    }
}
