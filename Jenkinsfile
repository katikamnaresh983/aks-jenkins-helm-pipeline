pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'yourdockerhubusername/sampleapp'
    }
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/yourusername/sampleapp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }
        stage('Push') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-password', variable: 'DOCKER_PASSWORD')]) {
                    sh 'echo $DOCKER_PASSWORD | docker login -u yourdockerhubusername --password-stdin'
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
        stage('Deploy to AKS') {
            steps {
                sh 'helm upgrade --install sampleapp helm-chart/ --set image.repository=$DOCKER_IMAGE'
            }
        }
    }
}
