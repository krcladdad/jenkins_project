
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/krcladdad/jenkins_project.git'
            }
        }
        stage('Run Python') {
            steps {
                sh 'python3 app.py'
            }
        }
    }
    post {
        success {
            sh '''
            curl -H 'Content-Type: application/json' \
            -d "{\"text\": \"✅ Build SUCCESS for Job: ${JOB_NAME} (#${BUILD_NUMBER}). View details: ${BUILD_URL}\"}" \
            https://capgemini.webhook.office.com/webhookb2/a5a0f2ad-b5f5-4f38-8ed5-e359635bb391@76a2ae5a-9f00-4f6b-95ed-5d33d77c4d61/IncomingWebhook/0edf770b4b8445c2869e042db1047300/31045307-ad26-4249-a2e4-cb5fc16412de/V22vX3EReBU9Wnrz6sbnW4G43k48qzVI3o74DKYR5AA341
            '''
        }
        failure {
            sh '''
            curl -H 'Content-Type: application/json' \
            -d "{\"text\": \"❌ Build FAILURE for Job: ${JOB_NAME} (#${BUILD_NUMBER}). View details: ${BUILD_URL}\"}" \
           https://capgemini.webhook.office.com/webhookb2/a5a0f2ad-b5f5-4f38-8ed5-e359635bb391@76a2ae5a-9f00-4f6b-95ed-5d33d77c4d61/IncomingWebhook/0edf770b4b8445c2869e042db1047300/31045307-ad26-4249-a2e4-cb5fc16412de/V22vX3EReBU9Wnrz6sbnW4G43k48qzVI3o74DKYR5AA341
            '''
        }
    }
}
