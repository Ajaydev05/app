

This project demonstrates containerization and CI/CD deployment of a MEAN stack application using Docker, Docker Compose, Jenkins, and Docker Hub. The frontend is served using Nginx, and the backend runs on Node.js.

---

# Project Architecture

* Frontend: Angular (served via Nginx)
* Backend: Node.js / Express
* Database: MongoDB (optional if used)
* Containerization: Docker
* Orchestration: Docker Compose
* CI/CD: Jenkins
* Image Registry: Docker Hub
* Web Server: Nginx

---

# Prerequisites

Install the following on your system:

* Docker
* Docker Compose
* Jenkins
* Git
* Docker Hub account

Verify installation:

```bash
docker --version
docker-compose --version
git --version
```

---

# Step 1: Clone the Repository

```bash
git clone https://github.com/Ajaydev05/app.git
cd app
```

---

# Step 2: Project Structure

```bash
app/
│
├── frontend/
│   ├── Dockerfile
│
├── backend/
│   ├── Dockerfile
│
├── docker-compose.yml
├── Jenkinsfile
└── README.md
```

---

# Step 3: Build Docker Images Manually

Frontend image build:

```bash
docker build -t ajaydev05/app1-frontend:latest ./frontend
```

Backend image build:

```bash
docker build -t ajaydev05/app1-backend:latest ./backend
```

---

# Step 4: Push Images to Docker Hub

Login to Docker Hub:

```bash
docker login
```

Push images:

```bash
docker push ajaydev05/app1-frontend:latest
docker push ajaydev05/app1-backend:latest
```

---

# Step 5: Run Application using Docker Compose

Start containers:

```bash
docker-compose up -d
```

Stop containers:

```bash
docker-compose down
```

Check running containers:

```bash
docker ps
```

Access application:

```bash
http://localhost
```

---

# Step 6: Jenkins CI/CD Setup

Open Jenkins:

```bash
http://localhost:8080
```

Create New Pipeline Job:

* Click New Item
* Enter job name
* Select Pipeline
* Click OK

Configure Pipeline:

* Select Pipeline Script from SCM
* SCM: Git
* Repository URL:

```bash
https://github.com/Ajaydev05/app.git
```

* Script Path:

```bash
Jenkinsfile
```

Save and Build.

---

# Step 7: Add Docker Hub Credentials in Jenkins

Go to:

Manage Jenkins → Manage Credentials → Global → Add Credentials

Enter:

* Kind: Username with password
* Username: your Docker Hub username
* Password: your Docker Hub password
* ID: dockerhub-credentials-id

Save.

---

# Step 8: Add Jenkins to Docker Group

Run on Jenkins server:

```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
```

---

# Step 9: Run Jenkins Pipeline

Click:

Build Now

Pipeline will:

* Clone repository
* Build Docker images
* Push images to Docker Hub
* Deploy using Docker Compose

---

# Step 10: Verify Deployment

Check containers:

```bash
docker ps
```

Check images:

```bash
docker images
```

Check logs:

```bash
docker logs frontend
docker logs backend
```

---

# Docker Hub Repository

Images available at:

```bash
https://hub.docker.com/r/ajaydev05
```

---

# CI/CD Workflow

1. Developer pushes code to GitHub
2. Jenkins detects changes
3. Jenkins builds Docker images
4. Jenkins pushes images to Docker Hub
5. Docker Compose deploys containers
6. Nginx serves frontend application

---

# Technologies Used

* Docker
* Docker Compose
* Jenkins
* Docker Hub
* Nginx
* Node.js
* Angular
* Git







<img width="1920" height="1080" alt="Screenshot 2026-02-24 183056" src="https://github.com/user-attachments/assets/22c14768-0d90-4251-a25b-535180c75966" />

<img width="1919" height="973" alt="Screenshot 2026-02-24 183110" src="https://github.com/user-attachments/assets/f2c27f5a-4448-4890-bb50-08681a3da4fe" />

<img width="1919" height="1015" alt="Screenshot 2026-02-24 183136" src="https://github.com/user-attachments/assets/f76f7e37-b99b-4618-919d-6079b46d3f7a" />

<img width="1919" height="1001" alt="Screenshot 2026-02-24 183234" src="https://github.com/user-attachments/assets/8181ee3b-9b53-4c28-b527-cad463d7ebeb" />

<img width="1919" height="999" alt="Screenshot 2026-02-24 183319" src="https://github.com/user-attachments/assets/2ad18501-6198-4714-9616-8027dc181983" />

