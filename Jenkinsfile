pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1116', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CB29DD325D6BCC57178C537B9BA9C39F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1116', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CB29DD325D6BCC57178C537B9BA9C39F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
