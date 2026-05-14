pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-abhi', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://EF29B5EEBF2B868D381410AE8C701791.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-abhi', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://EF29B5EEBF2B868D381410AE8C701791.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
