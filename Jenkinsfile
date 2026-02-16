pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(credentialsId: 'kubernetes') {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withKubeConfig(credentialsId: 'kubernetes') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
