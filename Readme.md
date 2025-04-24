# 🛠️ Jenkins CI/CD Pipeline with Docker

This project sets up a **Jenkins CI/CD pipeline** using Docker Compose. It includes:

- A `Jenkinsfile` defining stages: `Checkout`, `Build`, `Test`, and `Deploy`.
- A Docker Compose setup to run Jenkins in a container.

---

## 🚀 Jenkins Pipeline Overview

The `Jenkinsfile` defines the following stages:

```groovy
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment steps here
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

---

### ✅ Block 4: Docker Compose Configuration

```markdown
## 🐳 Docker Setup

### `docker-compose.yml` Configuration

```yaml
version: '3'

services:
  jenkins:
    image: jenkins/jenkins:lts
    container_name: jenkins
    ports:
      - "8080:8080"
      - "50000:50000"
    volumes:
      - jenkins_home:/var/jenkins_home
    environment:
      - JAVA_OPTS=-Djenkins.install.runSetupWizard=false
    restart: unless-stopped

volumes:
  jenkins_home:

---

### ✅ Block 6: Notes and Contributions

```markdown
## ✅ Useful Notes

- The pipeline runs on any available agent.
- Customize `Build`, `Test`, and `Deploy` stages according to your project.
- You can mount additional volumes or add plugins using a custom Jenkins Dockerfile if needed.

---

## 📬 Contributions & Feedback

Feel free to open issues or submit pull requests to enhance the pipeline or Docker setup.

---

Made with 💙 using Jenkins and Docker.


