# GitHub Actions ICE4

## Project Overview

This project is for practicing GitHub Actions. I created a Java Ant project in Apache NetBeans and added GitHub Actions workflows to the GitHub repository.

The purpose of this lab is to understand how automated workflows run in GitHub. I created two workflow files. The first one shows how jobs can depend on each other. The second one shows how jobs can run on different operating systems.

## Workflow 1: Dependent Jobs Workflow

The first workflow file is:

`.github/workflows/dependent-jobs.yml`

This workflow runs when changes are pushed to the `main` branch.

It has three jobs:

1. Build Job
2. Test Job
3. Deploy Job

The jobs run in this order:

Build Job to Test Job to Deploy Job

I used the `needs` key to make sure the jobs run in the correct order. The Test Job waits for the Build Job to finish. The Deploy Job waits for the Test Job to finish.

In this workflow, the build, test, and deploy steps are simulated using simple commands like `echo` and `sleep`.

## Workflow 2: Multi Platform Testing Workflow

The second workflow file is:

`.github/workflows/multi-platform.yml`

This workflow runs when a pull request is created to the `main` branch.

It has three jobs:

1. Ubuntu Job
2. Windows Job
3. macOS Job

Each job runs on a different operating system. I used `ubuntu-latest`, `windows-latest`, and `macos-latest`.

These jobs do not use the `needs` key, so they can run independently. Each job checks out the code, prints operating system information, creates a simple text file, and displays the file contents.

## Key Concepts Used

## needs

The `needs` key is used when one job has to wait for another job. I used it in the first workflow so the jobs run in the order build, test, and deploy.

## runs-on

The `runs-on` key tells GitHub which operating system to use for the job. I used Ubuntu, Windows, and macOS in the second workflow.

## env

The `env` key is used to create an environment variable. I used `PROJECT_NAME` in the workflow so it could be printed in the logs.

## Challenges Faced

One challenge I faced was understanding the difference between a workflow that runs on push and a workflow that runs on pull request. I learned that the first workflow runs when I push to the main branch, and the second workflow runs when I create a pull request.

Another challenge was understanding when to use `needs`. I learned that if I want jobs to run one after another, I should use `needs`. If I want jobs to run independently, I should not use `needs`.

I also had to be careful with YAML spacing because indentation matters in workflow files. If the spacing is wrong, the workflow may not run properly.

## Conclusion

This lab helped me understand how GitHub Actions can automate tasks in a repository. I learned how to create workflow files, run jobs in order, run jobs on different operating systems, and check the results from the Actions tab.
