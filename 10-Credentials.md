# Stage 10 — Credentials and Secrets

## Objective
Store and use secrets without hard-coding them in source code.

## Rules
- Never commit passwords, tokens, access keys, or private keys.
- Store secrets in Jenkins Credentials.
- Give credentials only the permissions needed.
- Avoid printing secrets in console output.
- Rotate secrets if they are exposed.

## Example
Create a **Secret text** credential with ID `demo-token` in a test Jenkins environment. Then use a Credentials Binding step to check whether it is available without printing its value.

```groovy
pipeline {
    agent any
    stages {
        stage('Check credential') {
            steps {
                withCredentials([
                    string(credentialsId: 'demo-token', variable: 'DEMO_TOKEN')
                ]) {
                    sh '''
                        test -n "$DEMO_TOKEN" &&
                        echo "Credential is available"
                    '''
                }
            }
        }
    }
}
```

This requires the Credentials Binding plugin and a credential with that ID. Use only a harmless test secret for the lab.

## Assignment
Explain why putting a token directly in a Jenkinsfile is unsafe.
