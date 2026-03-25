# Effective Mobile Test Task

## 📌 Description

This project demonstrates a simple web application deployed using Docker and Docker Compose.

The architecture consists of:

* Python backend (HTTP server)
* Nginx reverse proxy
* Internal Docker network

## 🏗 Architecture

```
Client → Nginx → Backend (Python)
```

* Backend listens on port **8080** (internal only)
* Nginx listens on port **80** (public)
* Communication is done via Docker network

## 🚀 Run the project

```bash
docker-compose up -d --build
```

Check:

```bash
curl http://localhost
```

Expected output:

```
Hello from Effective Mobile!
```

## 🐳 Docker Best Practices Used

* Official base images (`python:3.11-slim`, `nginx:alpine`)
* Minimal image size
* Non-root user for backend container
* Explicit `WORKDIR`
* Healthchecks for both services
* No unnecessary files in images
* Internal network isolation (backend not exposed)

## ➕ Notes

* Multi-stage build was not required due to simplicity of the application
* Backend is not exposed outside Docker network by design

## Troubleshooting

### 1. Docker won't start
Make sure the Docker daemon is running:
```bash
sudo systemctl start docker
```

## Improvements

- Added X-Forwarded-Proto header for correct scheme handling
- Optimized Docker build with .dockerignore
- Secured environment variables via .gitignore
- Improved nginx performance settings

## 📎 Author

```
mslav
```