# My -first-pipeline

```
pipeline {
    agent any

    stages {
        stage('Welcome') {
            steps {
                echo 'Welcome to Jenkins Learning from Scratch'
            }
        }

        stage('System Information') {
            steps {
                sh 'date'
                sh 'hostname'
                sh 'pwd'
            }
        }

        stage('Completion') {
            steps {
                echo 'First pipeline completed'
            }
        }
    }
}
```
