pipeline {
    agent any

    environment {
        PROJECT_ID = "rugged-alloy-482607-h2"
        CLUSTER_NAME = "gke-cluster"
        REGION = "us-central1"
    }

    stages {

        stage('Connect to GKE') {
            steps {
                sh '''
                gcloud container clusters get-credentials $CLUSTER_NAME \
                --region $REGION \
                --project $PROJECT_ID
                '''
            }
        }

        stage('Check Pods') {
            steps {
                sh 'kubectl get pods'
            }
        }

        stage('Check Services') {
            steps {
                sh 'kubectl get svc'
            }
        }

        stage('Check Deployments') {
            steps {
                sh 'kubectl get deployments'
            }
        }
    }
}
