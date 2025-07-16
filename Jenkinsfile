@Library('my-shared-lib-lab35') _

pipeline {
    agent { label 'worker-1' } 

    environment {
        IMAGE = "mohamed2200/jenkins-app:${env.BRANCH_NAME}"
        NAMESPACE = "${env.BRANCH_NAME}"
    }

    stages {
        stage('Build App') {
            steps {
                buildApp()
            }
        }

        stage('Build Docker Image') {
            steps {
                buildImage(IMAGE)
            }
        }

        stage('Push Image to DockerHub') {
            steps {
                pushImage(IMAGE)
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                deploy(NAMESPACE)
            }
        }
    }
}
