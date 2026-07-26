pipeline {
    agent any

    environment {
        IMAGE_NAME = "nadahamdallah/jenkins-app"
        IMAGE_TAG = "${BUILD_NUMBER}"
        DOCKER_CREDENTIALS = "dockerhub-creds"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: "${DOCKER_CREDENTIALS}",
                        usernameVariable: 'DOCKER_USERNAME',
                        passwordVariable: 'DOCKER_PASSWORD'
                    )
                ]) {

                    sh '''
                    echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
                    docker push ${IMAGE_NAME}:${IMAGE_TAG}
                    '''
                }
            }
        }

        stage('Delete Local Image') {
            steps {
                sh 'docker rmi ${IMAGE_NAME}:${IMAGE_TAG}'
            }
        }

        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }

    post {

        always {
            echo 'Pipeline Finished'
        }

        success {
            echo 'Deployment Successful'
        }

        failure {
            echo 'Pipeline Failed'
        }
    }
}
