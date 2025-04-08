# MERN Docker Compose App

A simple MERN (MongoDB, Express.js, React, Node.js) stack application containerized using Docker and Docker Compose.

## 🔧 Prerequisites

- Docker installed
- Docker Compose installed

---

## 🚀 Run with Docker Compose

To start the full stack app:

```sh
docker compose up -d
```
_______________________________________________________________________________________________________________________
# Manual Docker Instructions
If you prefer running containers manually instead of using Docker Compose, follow these steps:

## 1. Create a Docker Network
Create a custom network so containers can communicate:
```sh 
docker network create demo
```
## 2. Build and Run the Frontend
Navigate to the frontend folder:
```sh
cd mern/frontend
docker build -t mern-frontend .
```

Run the frontend container:
```sh
docker run --name=frontend --network=demo -d -p 5173:5173 mern-frontend
```
🔗 Access the frontend at: http://localhost:5173

## 3. Run MongoDB Container
Start a MongoDB container with data persistence:
```sh
docker run --network=demo --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest
```
💾 Replace ~/opt/data with your preferred local path to store MongoDB data.

## 4. Build and Run the Backend
Navigate to the backend folder:
```sh
cd mern/backend
docker build -t mern-backend .
```
Run the backend container:
```sh
docker run --name=backend --network=demo -d -p 5050:5050 mern-backend
```
🛠️ Backend will be accessible at: http://localhost:5050
________________________________________________________________________________________________________
##📁 Project Structure
mern-docker-compose/
│
├── mern/
│   ├── backend/          # Express + Node.js backend
│   └── frontend/         # React frontend
├── docker-compose.yml    # Docker Compose configuration
└── README.md             # Project documentation
_________________________________________________________________________________________________________
# 🧠 Tips
Make sure ports 5173, 5050, and 27017 are available.

Use docker ps to check running containers.

Use docker logs <container_name> to debug logs.

You can remove containers with docker rm -f <container_name> if needed.

