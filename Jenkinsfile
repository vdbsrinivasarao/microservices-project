pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'vdb-cluster', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://C7C4BD697BD89639BE17C4AADD77EBC5.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml --validate=false" 

                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'vdb-cluster', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://C7C4BD697BD89639BE17C4AADD77EBC5.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
