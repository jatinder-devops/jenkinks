# Jenkins Jobs

## Objective
Create a Freestyle job and understand build execution.

## Create a Freestyle job
1. Select **New Item**.
2. Enter `first-jenkins-job`.
3. Choose **Freestyle project**.
4. Add a build step called **Execute shell**.
5. Add these commands:
```bash
echo "My first Jenkins job"
date
whoami
hostname
df -h
```
6. Save, select **Build Now**, and open **Console Output**.

## Concepts
- A job defines work Jenkins should perform.
- A build is one run of the job.
- Build logs help diagnose failures.
- Build triggers decide when a job starts.

## Assignment
Create a second job that prints system information and explain each command.
