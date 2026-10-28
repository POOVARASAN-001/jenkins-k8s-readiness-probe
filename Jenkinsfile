
pipeline {
    agent any

    environment {
        KUBECTL = 'D:\\DockerApp\\resources\\bin\\kubectl.exe'
        KUBECONFIG = 'C:\\Users\\POOVARASAN\\.kube\\config'
    }

    stages {
        stage('Deploy Application') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
            }
        }

        stage('Verify Readiness Probe') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/readiness-app --timeout=180s'
                bat '"%KUBECTL%" get pods -l app=readiness-app'
                bat '"%KUBECTL%" describe deployment readiness-app'
            }
        }
    }
}
