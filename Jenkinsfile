pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(credentialsId: 'kubeconfig-ec2') {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withKubeConfig(credentialsId: 'kubeconfig-ec2') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
