pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "shibu08/mynodeapp"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Shubi2001/docker-mynodeapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:latest .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'shibu08', passwordVariable: 'Welcome(@#123)')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE:latest'
            }
        }
    }
}
