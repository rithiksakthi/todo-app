pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'myapp'  // Docker image name
        DOCKER_TAG = "latest"   // Tag name, you can customize this if needed
        REPO_NAME = 'rithik1007/todo-app'  // Your Docker Hub repository name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/rithiksakthi/todo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}")
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    docker.image("${DOCKER_IMAGE}:${DOCKER_TAG}").inside {
                        sh 'npm test'  // Replace with your app's test command
                    }
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Ensure your Docker Hub credentials are set in Jenkins
                    docker.withRegistry('', 'docker-token') {
                        // Correctly tag the image with your Docker Hub repository (rithik1007/todo-app)
                        sh "docker tag ${DOCKER_IMAGE}:${DOCKER_TAG} ${REPO_NAME}:${DOCKER_TAG}"

                        // Push the tagged image to Docker Hub
                        sh "docker push ${REPO_NAME}:${DOCKER_TAG}"
                    }
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    sh "docker run -d --name myapp -p 80:80 ${DOCKER_IMAGE}:${DOCKER_TAG}"  // Adjust port and options as needed
                }
            }
        }
    }

    post {
        always {
            sh "docker rmi ${DOCKER_IMAGE}:${DOCKER_TAG}"  // Clean up image
        }
    }
}


