# Stage 7 — # Stage 7 — Jenkinsfile

## Objective
Define a pipeline as code and store it with your project.

A `Jenkinsfile` is a text file that defines pipeline behavior. This example uses Declarative Pipeline syntax.

## Example
```groovy
pipeline {
    agent any

    stages {
        stage('Welcome') {
            steps {
                echo 'Welcome to Jenkins'
            }
        }

        stage('System Information') {
            steps {
                sh 'date'
                sh 'hostname'
            }
        }

        stage('Completion') {
            steps {
                echo 'Pipeline completed'
            }
        }
    }
}
```

## Key elements
- `pipeline`: Defines the pipeline.
- `agent any`: Allows Jenkins to select an available agent.
- `stages`: Groups the pipeline stages.
- `stage`: Names a logical step.
- `steps`: Contains the operations for a stage.
- `sh`: Executes a shell command on a Unix-like agent.

## Lab
Commit the Jenkinsfile to your repository, configure Jenkins to load it from SCM, and run it.

## Assignment
Add a stage that prints the current working directory with `pwd`.
## Objective
Define a pipeline as code and store it with your project.

A `Jenkinsfile` is a text file that defines pipeline behavior. This example uses Declarative Pipeline syntax.

## Example
```groovy
pipeline {
    agent any

    stages {
        stage('Welcome') {
            steps {
                echo 'Welcome to Jenkins'
            }
        }

        stage('System Information') {
            steps {
                sh 'date'
                sh 'hostname'
            }
        }

        stage('Completion') {
            steps {
                echo 'Pipeline completed'
            }
        }
    }
}
```

## Key elements
- `pipeline`: Defines the pipeline.
- `agent any`: Allows Jenkins to select an available agent.
- `stages`: Groups the pipeline stages.
- `stage`: Names a logical step.
- `steps`: Contains the operations for a stage.
- `sh`: Executes a shell command on a Unix-like agent.

## Lab
Commit the Jenkinsfile to your repository, configure Jenkins to load it from SCM, and run it.

## Assignment
Add a stage that prints the current working directory with `pwd`.
