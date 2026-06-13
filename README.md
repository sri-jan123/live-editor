# 🚀 Live Editor

A real-time collaborative code editor built using **Monaco Editor**, **Yjs**, and **Socket.IO**.

The application enables multiple users to edit code simultaneously using **CRDT (Conflict-free Replicated Data Types)** for conflict-free synchronization. While the editor demonstrates real-time collaboration concepts, the primary focus of this project is its **containerized deployment architecture using Docker and Microsoft Azure**.

---

## ✨ Features

- Real-time collaborative editing
- Conflict-free synchronization using Yjs (CRDT)
- Low-latency communication with Socket.IO
- VS Code-like editing experience with Monaco Editor
- Multi-stage Docker build
- Containerized backend deployment
- Azure Container Registry integration
- Azure Container Instances deployment

---

# 🛠 Tech Stack

## Application Layer

- React
- Monaco Editor
- Yjs
- y-monaco
- Socket.IO
- Node.js
- Express.js

## Infrastructure & Cloud

- Docker
- Multi-Stage Docker Builds
- Docker Hub
- Azure Container Registry (ACR)
- Azure Container Instances (ACI)

---

# 🔄 Collaboration Strategy

The application uses **Yjs**, which implements **CRDT (Conflict-free Replicated Data Types)**.

### Benefits

- Concurrent editing support
- Eventual consistency
- Conflict-free synchronization
- Real-time shared state

---

# 🏗 Infrastructure Architecture

<img width="1490" height="1300" alt="Screenshot 2026-06-13 212737" src="https://github.com/user-attachments/assets/06777338-f250-4170-a312-f92562f05410" />

# 📁 Project Structure

```text
live-editor/
│
├── frontend/
│
├── backend/
│
└── Dockerfile
```

---

# ⚙️ Frontend Build Process

Generate production assets:

```bash
cd frontend
npm run build
```

This creates:

```text
dist/
```

The generated frontend files are served through the backend container.

---

### Why Multi-Stage Builds?

- Smaller image size
- Better separation of concerns
- Build dependencies excluded from production image
- Faster deployment

---

# 🚀 Local Container Execution

Build image:

```bash
docker build -t live-editor .
```

Run container:

```bash
docker run -p 4000:3000 live-editor
```

Access the application:

```text
http://localhost:4000
```

---

# 📦 Docker Hub

Push image to Docker Hub:

```bash
docker tag live-editor <dockerhub-username>/live-editor

docker push <dockerhub-username>/live-editor
```

Docker Hub acts as the external image registry.

---

# ☁️ Azure Container Registry (ACR)

A private Azure Container Registry was created for storing container images.

Example:

```text
livea.azurecr.io
```

Login:

```bash
docker login livea.azurecr.io
```

Tag image:

```bash
docker tag live-editor livea.azurecr.io/live-editor
```

Push image:

```bash
docker push livea.azurecr.io/live-editor
```

---

# ☁️ Azure Container Instances (ACI)

The application is deployed using **Azure Container Instances**.

ACI pulls the image directly from Azure Container Registry and hosts the container without requiring:

- Virtual Machines
- Kubernetes clusters
- Manual infrastructure management

### Benefits

- Serverless container hosting
- Fast deployment
- Reduced operational overhead
- Pay-per-use pricing model

---

# 📄 License

This project is licensed under the MIT License.
