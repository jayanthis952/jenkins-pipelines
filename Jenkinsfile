pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // add build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // add test steps here
                // sh 'exit 1'   // uncomment to simulate failure
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // add deploy steps here
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
            echo "Pipeline finished (success or failure)."
        }
    }
}
