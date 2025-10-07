pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                script {
                    echo "Testing the application..."
                    echo "Executing pipeline for branch ${BRANCH_NAME}"
                }
            }
        }

        stage('Build') {
            when {
                expression { BRANCH_NAME == 'main' }
            }
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage('Deploy') {
            when {
                expression { BRANCH_NAME == 'main' }
            }
            steps {
                script {
                    echo "Deploying the application..."
                }
            }
        }
    }

    post {
        success {
            script {
                def payload = [
                    content: "✅ Build SUCCESS on ${env.BRANCH_NAME}\n🔗 URL: ${env.BUILD_URL}"
                ]
                httpRequest(
                    httpMode: 'POST',
                    contentType: 'APPLICATION_JSON',
                    requestBody: groovy.json.JsonOutput.toJson(payload),
                    url: 'https://discordapp.com/api/webhooks/1425115614770364486/LTURxv3r2FHblGkP4Yn88izAMzqzF8qaXHRYP3ART7NN881La7P_fV65o6inidvMqYud'
                )
            }
        }

        failure {
            script {
                def payload = [
                    content: "❌ Build FAILED on ${env.BRANCH_NAME}\n🔗 URL: ${env.BUILD_URL}"
                ]
                httpRequest(
                    httpMode: 'POST',
                    contentType: 'APPLICATION_JSON',
                    requestBody: groovy.json.JsonOutput.toJson(payload),
                    url: 'https://discordapp.com/api/webhooks/1425115614770364486/LTURxv3r2FHblGkP4Yn88izAMzqzF8qaXHRYP3ART7NN881La7P_fV65o6inidvMqYud'
                )
            }
        }
    }
}
