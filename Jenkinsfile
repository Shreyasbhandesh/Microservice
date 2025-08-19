pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://F66FB72D14D78F20F5A11163A8D7E600.gr7.ap-south-1.eks.amazonaws.com']])  {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://F66FB72D14D78F20F5A11163A8D7E600.gr7.ap-south-1.eks.amazonaws.com']])  {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
