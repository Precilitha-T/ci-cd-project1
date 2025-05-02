# 🐳 CI/CD Pipeline with GitHub Actions & Docker (Local Deployment)

This project demonstrates a complete CI/CD pipeline using **GitHub Actions**, **Docker**, and **Docker Hub**, with deployment on a **local VM** — no cloud provider needed.


## 🚀 Project Objective

- Automatically build a Docker image on every `push` to the `main` branch
- Push the built image to **Docker Hub**
- Deploy and run the image on a **local VM** using Docker

---

## 🛠️ Tools Used

- [GitHub Actions](https://github.com/features/actions) – for CI/CD automation
- [Docker](https://www.docker.com/) – containerization and deployment
- [Docker Hub](https://hub.docker.com/) – to store images
- Local VM (Ubuntu/Linux) – for deployment (no cloud)


## 📁 Project Structure

ci-cd-project/
│
├── app.py # Sample Flask app
├── Dockerfile # Docker image definition
├── docker-compose.yml # (optional) for local multi-container setup
├── requirements.txt # Python dependencies
└── .github/
└── workflows/
└── docker.yml # GitHub Actions CI/CD workflow

## Process

Step 1: Create Project Folder & Files
bash
Copy
Edit
mkdir -p ci-cd-docker-vm/.github/workflows
cd ci-cd-docker-vm

touch app.py requirements.txt Dockerfile docker-compose.yml .github/workflows/ci-cd.yml

 Step 2: Edit app.py
bash
Copy
Edit
nano app.py

Step 3: Edit requirements.txt
bash
Copy
Edit
nano requirements.txt

 Step 4: Edit Dockerfile
bash
Copy
Edit
nano Dockerfile



## 🔄 GitHub Actions Workflow

### Trigger:  
Push to the `main` branch

### Steps:
1. Checkout code
2. Log in to Docker Hub using GitHub secrets
3. Build and push Docker image to Docker Hub

---

## 🔐 GitHub Secrets Required

Go to your GitHub repo → **Settings → Secrets and Variables → Actions**, and add:

| Name             | Value                             |
|------------------|------------------------------------|
| `DOCKER_USERNAME` | Your Docker Hub username (e.g., `precilitha10`) |
| `DOCKER_PASSWORD` | Docker Hub access token (starts with `dckr_pat_...`) |

---

## 🧪 Test Locally on Your VM

### 1. Pull the Docker image:

```bash
docker login             # Use your Docker username and access token
docker pull precilitha10/ci-cd-vm:latest

2. Run the container:
bash
Copy
Edit
docker run -d -p 5000:5000 precilitha10/ci-cd-vm:latest
3. Visit the app in your browser:
arduino
Copy
Edit
http://localhost:5000
📸 Deliverables
✅ GitHub repository with working CI/CD pipeline

✅ Docker image: precilitha10/ci-cd-vm

✅ Local deployment screenshots (add below if available)

✅ CI/CD pipeline status shown in Actions tab

