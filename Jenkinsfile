pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-4', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://09E647B6625FE912CD6E4A4C49CEAF1B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-4', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://09E647B6625FE912CD6E4A4C49CEAF1B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
