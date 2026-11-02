```
pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Validate') {
            steps {
                echo 'Validate source and configuration'
            }
        }

        stage('Build') {
            steps {
                echo 'Replace this with your real build command'
            }
        }

        stage('Test') {
            steps {
                echo 'Replace this with your real test command'
            }
        }
    }
}
```
