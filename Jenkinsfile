pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                script {
                    env.KUBECONFIG = '/home/ayadinou/.kube/config'
                    // Set the Minikube server address
                    def minikubeServer = 'ayadinou@192.168.1.9'

                    // SSH to the Minikube server and retrieve certificates
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ${minikubeServer} 'cat /home/ayadinou/.minikube/ca.crt' > ca.crt"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ${minikubeServer} 'cat /home/ayadinou/.minikube/profiles/minikube/client.crt' > client.crt"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ${minikubeServer} 'cat /home/ayadinou/.minikube/profiles/minikube/client.key' > client.key"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ${minikubeServer} 'cat $KUBECONFIG' > ~/.kube/config"

                }
            }
        }

        stage('Deploy to Minikube') {
            steps {
                script {
                    // Use kubectl to interact with the Minikube cluster
                    

                    // Your deployment steps go here
                    // Example: Deploy a Kubernetes manifest file
                    sh 'kubectl get pods'
                }
            }
        }
/*
        stage('Run Tests') {
            steps {
                script {
                    // Example: Run tests against the deployed application
                    // You can customize this based on your testing framework
                    sh 'kubectl wait --for=condition=available deployment/your-app --timeout=300s'
                    sh 'kubectl exec -it deployment/your-app -- /path/to/your/test/script.sh'
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment and tests passed successfully!'
        }
        failure {
            echo 'Deployment or tests failed!'
        }
    } */
    }
}
