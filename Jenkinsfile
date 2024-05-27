pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3BE89C723B4311D6E03113BE3C0A1C08.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl apply -f deployment-service.yml"
                   sleep 60
               }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3BE89C723B4311D6E03113BE3C0A1C08.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get all -n webapps"
                }   
            }
        }
    }
}
