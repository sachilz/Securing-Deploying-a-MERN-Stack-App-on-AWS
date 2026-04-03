# 🚀 Containerized MERN Stack with Nginx Reverse Proxy

A professional-grade full-stack application demonstrating **Microservices Architecture**, **Containerization**, and **Advanced Networking** using Docker and Nginx.

---

## 🏗️ Project Architecture

This project isn't just about code; it's about how the system communicates. The architecture follows a "Flow-Wise" deployment strategy:

- **Frontend:** React.js (SPA)
- **Backend:** Node.js & Express.js API
- **Database:** MongoDB Atlas (Cloud)
- **Reverse Proxy:** Nginx
- **Orchestration:** Docker Compose

---

## 🛠️ Key Technical Features

### 1. Dockerization & Orchestration
The entire stack is containerized using optimized Dockerfiles. Using **Docker Compose**, the environment is spun up with a single command, ensuring "it works on my machine" works everywhere.

### 2. Nginx Reverse Proxy
Nginx acts as the gatekeeper (Entry Point). It:
- Serves static React frontend files.
- Routes `/api` requests dynamically to the Node.js backend container.
- Handles request headers and prevents CORS issues in a production-like setup.

### 3. Service Discovery & Networking
Instead of using `localhost`, the services communicate via a custom **Docker Bridge Network**. 
- The Frontend talks to `http://backend:5000` (using the container name).
- This mimics real-world production environments where IP addresses are dynamic.

### 4. API Testing
All RESTful endpoints were rigorously tested using **Postman** to ensure schema validation and correct HTTP status codes (200 OK, 201 Created) before being integrated with the UI.

---

## 📁 Project Structure

Below is the organized structure of the project, separating the concerns of the frontend, backend, and infrastructure configuration:

```text
MERN STACK
├── 📂 backend
│   ├── 📂 models
│   ├── 📂 node_modules
│   ├── .gitignore
│   ├── Dockerfile
│   ├── package-lock.json
│   ├── package.json
│   └── server.js
├── 📂 frontend
│   ├── 📂 node_modules
│   ├── 📂 public
│   ├── 📂 src (App.js, index.js, etc.)
│   ├── .gitignore
│   ├── Dockerfile
│   ├── package-lock.json
│   ├── package.json
│   └── README.md
├── 🐳 docker-compose.yml
└── ⚙️ nginx.conf
```
## 🚀 Getting Started
### Prerequisites
- Docker & Docker Compose installed
- MongoDB Atlas Connection String

## Installation & Deployment
### Clone the repository:
```
git clone https://github.com/sachilz/dockerized-mern-app
cd your-repo-name
```

### Run with Docker Compose:
```
docker compose up --build
```

### Access the App:
- Frontend/App: http://localhost:80
- Backend API: http://localhost/api

#### 👨‍💻 Developed by Sachintha Dilshan - DevOps Enthusiast
