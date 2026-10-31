# Stage 6 — Git and GitHub Integration

## Objective
Retrieve source code from GitHub in a Jenkins pipeline.

## Concepts
- Git tracks file history.
- GitHub hosts Git repositories.
- Checkout retrieves repository content for a build.
- A branch identifies a line of development.

## Lab
1. Create a small public GitHub repository containing `README.md`.
2. Create a Pipeline job in Jenkins.
3. Configure **Pipeline script from SCM** and select Git.
4. Enter the repository URL and branch.
5. Set the script path to `Jenkinsfile` and run the job.

Public repositories can be used without private-repository credentials. For private repositories, use an appropriately scoped credential stored in Jenkins.

## Assignment
Make a commit to your repository and verify that Jenkins checks out the expected revision.
