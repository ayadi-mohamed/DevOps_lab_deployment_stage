pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                script {
                    env.KUBECONFIG = '~/.kube/config'
                    // Set the Minikube server address
                    sh "sshpass -p ayadinou1601 scp ayadinou@192.168.1.9:/home/ayadinou/deployment_devops/config ~/.kube/config"
                    // SSH to the Minikube server and retrieve certificates
                    sh "sshpass -p ayadinou1601 scp -o StrictHostKeyChecking=no ayadinou@192.168.1.9:/home/ayadinou/.minikube/ca.crt /var/jenkins_home/.kube/ca.crt"
                    sh "sshpass -p ayadinou1601 scp -o StrictHostKeyChecking=no ayadinou@192.168.1.9:/home/ayadinou/.minikube/profiles/minikube/client.crt /var/jenkins_home/.kube/client.crt"
                    sh "sshpass -p ayadinou1601 scp -o StrictHostKeyChecking=no ayadinou@192.168.1.9:/home/ayadinou/.minikube/profiles/minikube/client.key /var/jenkins_home/.kube/client.key"
                   // sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ${minikubeServer} 'cat $KUBECONFIG' > ~/.kube/config"

                }
            }
        }

        stage('Deploy to kubernetes cluster') {
            steps {
                script {
                    // Use kubectl to interact with the Minikube cluster
                    
                   // sh "sshpass -p ayadinou1601 scp *.yaml ayadinou@192.168.1.9:/home/ayadinou/deployment_devops"
                    // Your deployment steps go here
                    // Example: Deploy a Kubernetes manifest file
                    /*
                   sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl delete ns mysql"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl delete ns pet-owner"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl create ns pet-owner"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl apply -f /home/ayadinou/deployment_devops/deployment.yaml"

                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl apply -f /home/ayadinou/deployment_devops/service_pet.yaml"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl create ns mysql"

                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl apply -f /home/ayadinou/deployment_devops/deployment_mysql.yaml"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl apply -f /home/ayadinou/deployment_devops/sercice_mysql.yaml"
                    sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ayadinou@192.168.1.9 kubectl apply -f /home/ayadinou/deployment_devops/pvc.yaml" */

                   // sh "kubectl config use-context minikube"
                    sh "cat $(KUBECONFIG)"
                    sh "sleep 5 && export KUBECONFIG=~/.kube/config"
                    sh " kubectl config get-clusters"
                    sh "kubectl config view && echo $KUBECONFIG"
                    sh "kubectl delete ns mysql"
                    sh "kubectl delete ns pet-owner"
                    sh "kubectl create ns pet-owner"
                    sh "kubectl apply -f deployment.yaml"
                    sh "kubectl apply -f service_pet.yaml"
                    sh "kubectl create ns mysql"
                    sh "kubectl apply -f deployment_mysql.yaml"
                    sh "kubectl apply -f sercice_mysql.yaml"
                    sh "kubectl apply -f pvc.yaml"

                 //   sh 'sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ${minikubeServer} kubectl create deployment --image=ayadinou/tp_devops_spring_boot_app -n pet-owner -- '
                   // sh 'sh "sshpass -p ayadinou1601 ssh -o StrictHostKeyChecking=no ${minikubeServer} kubectl create deployment --image=ayadinou/tp_devops_spring_boot_app -n pet-owner '

                    
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
