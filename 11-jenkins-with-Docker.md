# Stage 11 — Jenkins with Docker

## Objective
Build and verify a Docker image from a Jenkins pipeline.

## Example Dockerfile
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```

Add an `index.html` file to the same repository.

## Example Jenkinsfile
```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build image') {
            steps {
                sh 'docker build -t jenkins-demo:latest .'
            }
        }
        stage('Verify image') {
            steps {
                sh 'docker image inspect jenkins-demo:latest'
            }
        }
    }
}
```

Docker must be installed and accessible from the agent. Access to the Docker daemon can grant extensive privileges, so use an appropriately isolated build environment. This example builds locally; it does not push or deploy the image.

## Assignment
Extend the pipeline to tag and publish an image to a registry using Jenkins credentials.
