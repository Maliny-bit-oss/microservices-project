pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: '']]) {https://95246BDED4E3A7180B5838DC56F013DE.gr7.us-east-1.eks.amazonaws.com
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: '']]) {https://95246BDED4E3A7180B5838DC56F013DE.gr7.us-east-1.eks.amazonaws.com
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
