pipeline {
    agent any

    environment {
        GITHUB_REPO = "https://github.com/anshsehgal13/ChatBotApp"  // Replace with your GitHub repo URL
        NODE_VERSION = "v18.20.6"  
        RENDER_API_KEY = "rnd_qXmPDBgzdjGTrvsQRnZcqoz8Z22k"  // Replace with your Render API key
        RENDER_SERVICE_ID = "csmisrrtq21c73aja8v0"  // Updated Render service ID
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: "${GITHUB_REPO}"
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install dependencies from the root package.json
                    sh 'npm install'
                }
            }
        }

        stage('Build App') {
            steps {
                script {
                    // Build the app (run the 'build' script from package.json)
                    sh 'npm run build'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Placeholder for testing (add tests as per your setup)
                    sh 'echo "Running tests (Dummy Stage)"'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy to Render using the Render API
                    sh 'curl -X POST -H "Accept: application/json" -H "Authorization: Bearer ${RENDER_API_KEY}" https://api.render.com/v1/services/${RENDER_SERVICE_ID}/deploys'
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
