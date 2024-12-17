pipeline {
    agent any
    environment {
        DOCKER_CRED = credentials('docker-token')
    }

    stages {
        stage('Build image') {
            steps {
                sh 'docker build -t rithik1007/todo-app:${BUILD_ID} .'
                sh 'docker images'
            }
        }

        stage('Push Docker hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-token', usernameVariable: 'DOCKER_CRED_USR', passwordVariable: 'DOCKER_CRED_PSW')]) { 
                    sh 'docker login -u ${DOCKER_CRED_USR} -p ${DOCKER_CRED_PSW}' 
                    sh 'docker push rithik1007/todo-app:${BUILD_ID}'
                }
            }
        }

        stage('Deploy to Server') {
            steps {
                echo 'Application deployed successfully!' // Print a message instead of executing deployment commands
            }
        }
    }

    post {
        always {
            sh 'docker image prune -a --force'
        }
    }
}

