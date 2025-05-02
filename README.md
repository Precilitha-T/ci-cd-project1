# 🐳 CI/CD Pipeline with GitHub Actions & Docker (Local Deployment)

This project demonstrates a complete CI/CD pipeline using **GitHub Actions**, **Docker**, and **Docker Hub**, with deployment on a **local VM** — no cloud provider needed.


## 🚀 Project Objective

- Automatically build a Docker image on every `push` to the `main` branch
- Push the built image to **Docker Hub**
- Deploy and run the image on a **local VM** using Docker


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

**Step 1**: Create Project Folder & Files
bash
mkdir ci-cd-project
cd ci-cd-project

touch app.py requirements.txt Dockerfile docker-compose.yml .github/workflows/ci-cd.yml

**Step 2**: Edit app.py
bash
vi app.py

**Step 3**: Edit requirements.txt
bash
vi requirements.txt

**Step 4**: Edit Dockerfile
bash
vi Dockerfile


**Step 4**: Initialize Git & Push to GitHub
bash
git init
git remote add origin https://github.com/your-username/your-repo-name.git
git add .
git commit -m "Initial commit - CI/CD setup"
git branch -M main
git push -u origin main


**Step 5**: Create GitHub Actions Workflow
bash
mkdir -p .github/workflows
vi .github/workflows/docker.yml

Replace your_dockerhub_username with your actual Docker Hub username.
Save and exit.

**Step 6**: To push the workflows into the github

git add .github/workflows/docker.yml
git commit -m "Add CI/CD workflow"
git push

**Step 7**: Set Secrets on GitHub
In your GitHub repo:

Go to Settings → Secrets and variables → Actions → New repository secret
Add:
Name: DOCKER_USERNAME
Value: your Docker Hub username (e.g., precilitha123)
Do the same for your password:

Name: DOCKER_PASSWORD
Value: your Docker Hub password or access token(better to create access token and use that)

To create access token: Dockerhub account --> On profile click on Account settings --> Personal Access Tokens --> Generate new token --> Give some token description(name) --> Now, change Access permissions as read & write --> Generate --> copy the token and use it in github secrets


**Step 8**: Set Up Local VM for Deployment
On your VM:
bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

Add your user to Docker group:
bash
sudo usermod -aG docker $USER
Log out & log back in for group changes to apply.

## 🧪 Test Locally on Your VM
**Step 9**: Deploy the App on Your VM
On your VM:
## Pull the Docker image:
bash

docker login
give username and token

docker pull your_dockerhub_username/ci-cd-vm:latest
docker run -d -p 5000:5000 your_dockerhub_username/ci-cd-vm:latest

Access the app in your browser:
bash
http://<your-vm-ip>:5000
Use ip a or hostname -I to get your VM's IP.



📸 Deliverables
✅ GitHub repository with working CI/CD pipeline

✅ Docker image: precilitha10/ci-cd-vm

✅ Local deployment screenshots (add below if available)

✅ CI/CD pipeline status shown in Actions tab

## Results:


![Screenshot (287)](https://github.com/user-attachments/assets/f84e2020-a08e-49ad-b617-1ce88c356cb1)

![Screenshot (288)](https://github.com/user-attachments/assets/ae4759e7-9ba8-45b3-b64d-813972c6fe28)

![Screenshot (289)](https://github.com/user-attachments/assets/a6b21bc2-8cc2-4d4e-9c46-978215b439d0)

![Screenshot (291)](https://github.com/user-attachments/assets/49e298b0-09e0-4c10-8a91-7d2d2375147d)

![Screenshot (297)](https://github.com/user-attachments/assets/1e3afac0-b94c-44dc-9b81-de4c6c478f17)

![Screenshot (298)](https://github.com/user-attachments/assets/1bf8f0fa-bd20-4886-8e79-78b3ed52e675)
