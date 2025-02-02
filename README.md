# To-Do Application with CI/CD Pipeline

This project implements a simple **To-Do web application** using **Docker**, **Jenkins**, and **Docker Compose** to automate and streamline the development process.

## Features:
- **Containerization**: The app is containerized using Docker for consistency across environments.
- **CI/CD Pipeline**: Jenkins automates the build, test, and deployment processes.
- **Docker Compose**: Ensures seamless communication between services like the app, database, and other containers.

## Setup Instructions:
1. **Build Docker Image**: Use the Dockerfile to build the container.
2. **Run Tests**: Automated tests are run in the pipeline.
3. **Push to Docker Hub**: The image is pushed to Docker Hub after successful testing.
4. **Deploy**: The app is deployed to a production environment after the build.

## Prerequisites:
- Docker
- Jenkins
- Docker Hub account (for pushing images)

## Conclusion:
This project demonstrates how to automate deployment and testing for a To-Do app using best practices in DevOps.

