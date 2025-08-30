# Day 3: Automating Jenkins Builds with Ngrok, GitHub Webhooks & Jenkinsfile

Today we will learn how to write **JenkinsFile** and **automate Jenkins builds** using **Ngrok** and **GitHub Webhooks**, instead of manually clicking “Build Now”.
By the end, you’ll understand how Ngrok exposes your local Jenkins, how GitHub webhooks notify Jenkins, and how Jenkinsfile defines your pipeline.

## Prerequisites

- Jenkins running locally (see Day 1 setup with Docker)

- A GitHub repository connected to Jenkins

- Ngrok installed and configured

- A basic Jenkins Multibranch Pipeline created (see Day 2)

## Step 1: Understanding Ngrok

- The laptop is running Jenkins on http://localhost:8080.
- GitHub needs a way to notify Jenkins about code changes, but Jenkins on localhost:8080 is only accessible to us locally and not from the internet.
- In that case, we will use something known as **Ngrok**
- It is a tool that creates temporary public URL for our local Jenkins
- With this URL, we can connect github to Jenkins
- You can install ngrok by visiting this doc below:
  <a href = https://dashboard.ngrok.com/get-started/setup/linux>Ngrok</a>

## Step 2: Setting up Github Webhook

- A GitHub webhook is a way for GitHub to notify Jenkins whenever you push code.
- We can set up Github Webhook like this:

  1. Go to your GitHub repository → Settings → Webhooks.

  2. Click Add Webhook.

  3. Enter your Ngrok URL with /github-webhook/ at the end:

  ```

  https://random-id.ngrok-free.app/github-webhook/

  ```

  4. Make sure the **content type** is application/json
  5. Select **Just the push event** and save it

- Now, every time you push code → GitHub sends a JSON message to Jenkins.

## Step 3: Setting up JenkinsFile

- A Jenkinsfile defines what steps your pipeline should run after each build trigger.

- Without it, Jenkins knows when to build but not what to do.

- There are two syntaxes for JenkinsFile

  1. Declarative Syntax(easier and most recommended for beginners)
  2. Scripted Syntax(difficult and less common for basic setups)

- Syntax of JenkinsFile:

```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
```
