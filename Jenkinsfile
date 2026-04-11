pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-abhi', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://FEA6EF663BA134EF92AA196ED2764700.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-abhi', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://FEA6EF663BA134EF92AA196ED2764700.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
