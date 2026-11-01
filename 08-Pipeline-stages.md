# Stage 8 — Pipeline Stages

## Objective
Organize a pipeline into logical stages and understand stage results.

## Example
See the `Jenkinsfile` in this directory for a sample pipeline.

Typical application stages include:
1. Checkout
2. Build
3. Test
4. Package
5. Deploy

A stage named `Test` does not automatically test an application: you must add the actual test command. If a stage fails, later stages are normally skipped unless failure handling changes that behavior.

## Lab
Create a pipeline with five stages. Initially use `echo` statements, then replace them with real commands for a project you understand.

## Assignment
Explain which stages should prevent a production deployment if they fail.
```
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout stage demonstration'
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage demonstration'
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage demonstration'
            }
        }

        stage('Package') {
            steps {
                echo 'Package stage demonstration'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage demonstration'
            }
        }
    }
}
```
