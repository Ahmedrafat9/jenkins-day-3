pipeline {
    agent any

    environment {
        KUBECONFIG = "${HOME}/.kube/config"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Debug Workspace') {
            steps {
                sh 'ls -al'
                sh 'ls -al k8s'
            }
        }
        stage('Deploy to Minikube') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
            }
        }
                

        stage('Verify') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}
