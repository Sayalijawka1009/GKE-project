pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:v1 .'
            }
        }

        stage('Push Image') {
            steps {
                sh '''
                docker tag myapp:v1 us-central1-docker.pkg.dev/qwiklabs-gcp-01-3b47ca77e2ae/my-repo/myapp:v1
                docker push us-central1-docker.pkg.dev/qwiklabs-gcp-01-3b47ca77e2ae/my-repo/myapp:v1
                '''
            }
        }

        stage('Deploy to GKE') {
            steps {
                sh '''
                kubectl apply -f deployment.yaml
                kubectl apply -f service.yaml
                '''
            }
        }
    }
}
