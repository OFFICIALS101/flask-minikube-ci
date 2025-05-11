
# Flask App Deployment on Minikube via GitHub Actions CI/CD (Azure VM + Terraform)

This project demonstrates how to build, containerize, and deploy a simple Flask application to a Minikube cluster running on an Azure Virtual Machine using Terraform and GitHub Actions.

---

## 🚀 Project Overview

We automate the deployment of a Dockerized Flask application using:

- **Terraform** for provisioning an Azure VM
- **Minikube** as the Kubernetes cluster
- **GitHub Actions** for CI/CD
- **Docker Hub** to store the application image

---

## 🧱 Tech Stack

- **Flask (Python)** – Web application
- **Docker** – Containerization
- **Terraform** – Infrastructure as Code
- **Minikube** – Kubernetes Cluster
- **GitHub Actions** – CI/CD Pipeline
- **Azure** – Cloud provider (VM hosting Minikube)

---

## 🗂️ Project Structure

```bash
flask-minikube-ci/
├── app/
│   ├── app.py
│   └── requirements.txt
├── Dockerfile
├── main.tf
├── variables.tf
├── outputs.tf
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── .github/
│   └── workflows/
│       └── ci-cd.yml
└── README.md
```

---

## 🛠️ Terraform Azure Setup

1. **Create Azure VM** with Terraform:
   ```bash
   terraform init
   terraform plan
   terraform apply
   ```
2. **SSH into the VM** and install:
   - Docker
   - Minikube
   - kubectl

---

## 🐳 Docker & Flask App

- Simple Flask app served via `app.py`
- Containerized with a basic Dockerfile:
  ```Dockerfile
  FROM python:3.9-slim
  WORKDIR /app
  COPY requirements.txt .
  RUN pip install -r requirements.txt
  COPY . .
  CMD ["python", "app.py"]
  ```

- Pushed to Docker Hub:
  🔗 [officials101/my-python-app](https://hub.docker.com/r/officials101/my-python-app)

---

## 📦 Kubernetes Deployment

Files inside the `k8s/` directory:
- `deployment.yaml` – Defines the app deployment
- `service.yaml` – Exposes the app on port 5000

Deploy via:
```bash
kubectl apply -f k8s/
```

---

## 🔄 GitHub Actions Workflow

`.github/workflows/ci-cd.yml` automates the process:

- Triggers on push to `main`
- Builds Docker image
- Pushes to Docker Hub
- SSH into Azure VM
- Deploys to Minikube

Example snippet:
```yaml
- name: Deploy to Minikube
  run: ssh azureuser@<your-vm-ip> 'kubectl apply -f deployment.yaml'
```

---

## 📸 Screenshots

> Include your screenshots here:
- Terraform Apply
- Docker Image Build
- GitHub Actions Success
- Minikube Running
- Application in Browser

---

## 🔗 Resources

- Docker Image: [`officials101/my-python-app`](https://hub.docker.com/r/officials101/my-python-app)
- GitHub Repo: [`github.com/OFFICIALS101/flask-minikube-ci`](https://github.com/OFFICIALS101/flask-minikube-ci)

---

## 📝 Author

Ayoade Josiah Ayomide  
_Cloud & DevOps Enthusiast | Info Systems Student | IT Support | Cybersecurity Learner_

---

## 📌 Hashtags (for LinkedIn/Instagram)

```
#DevOps #CI_CD #Terraform #GitHubActions #Minikube #Kubernetes #Docker #Azure #Python #Flask #CloudEngineering #StudentDeveloper #TechNigeria
```

