
```
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t jenkins-demo:latest .'
            }
        }

        stage('Verify Image') {
            steps {
                sh 'docker image inspect jenkins-demo:latest'
            }
        }
    }
}
```
