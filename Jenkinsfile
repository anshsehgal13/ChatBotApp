pipeline {
    agent any

    environment {
        GITHUB_REPO = "https://github.com/anshsehgal13/ChatBotApp.git"
        RENDER_API_KEY = "rnd_qXmPDBgzdjGTrvsQRnZcqoz8Z22k"  // Replace with actual API key
        RENDER_SERVICE_ID = "csmisrrtq21c73aja8v0"  // Replace with actual service ID
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: "https://github.com/anshsehgal13/ChatBotApp/"
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build Project') {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    sh 'echo "No tests defined, skipping..."'
                }
            }
        }

        stage('Deploy to Render') {
            steps {
                script {
                    sh '''
                    curl -X POST -H "Accept: application/json" \
                         -H "Authorization: Bearer ${RENDER_API_KEY}" \
                         https://api.render.com/v1/services/${RENDER_SERVICE_ID}/deploys
                    '''
                }
            }
        }
    }

    post {
        success {
            echo '✅ Deployment Successful!'
        }
        failure {
            echo '❌ Deployment Failed!'
        }
    }
}
