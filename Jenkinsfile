pipeline {
    agent any

    environment {
        // Set environment variables for Azure Container Registry
        ACR_LOGIN_SERVER = '<your_acr_login_server>'
        ACR_REPO_NAME = 'node-cicd-app'
        AZURE_CREDENTIALS_ID = '<azure-service-principal-credentials-id>' // Jenkins credentials for Azure service principal
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from the repository
                git branch: 'main', url: 'https://github.com/yourusername/cicd-pipeline-azure-jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${ACR_LOGIN_SERVER}/${ACR_REPO_NAME}:latest")
                }
            }
        }

        stage('Push Docker Image to ACR') {
            steps {
                script {
                    docker.withRegistry("https://${ACR_LOGIN_SERVER}", AZURE_CREDENTIALS_ID) {
                        docker.image("${ACR_LOGIN_SERVER}/${ACR_REPO_NAME}:latest").push()
                    }
                }
            }
        }

        stage('Deploy to AKS') {
            steps {
                script {
                    // Use Azure CLI to deploy the application to AKS
                    sh '''
                    az aks get-credentials --resource-group <aks-resource-group> --name <aks-cluster-name>
                    kubectl apply -f k8s-deployment.yaml
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}