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
