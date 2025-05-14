pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-cluster', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://C157FFD450FAD984E3A210D31083BF93.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml" 

                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-cluster', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://C157FFD450FAD984E3A210D31083BF93.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
