# flask-docker-app

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Flask](https://img.shields.io/badge/Flask-Backend-black)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED)

## 🚀 Project Overview
A lightweight **Flask** backend application packaged as a **production-friendly Docker image**. This repository demonstrates how to structure, containerize, and run a simple Flask service consistently across environments (local → CI → cloud).

> **Why this matters:** Containerization removes "it works on my machine" issues and enables repeatable builds and deployments.

---

## 📌 Features
- Flask-based backend
- Dockerized for easy deployment
- Lightweight image using `python:3.8-alpine`
- REST API support

---

## 🧭 API Endpoints (Examples)
> Endpoints may vary depending on the app implementation. Use these examples as a template and adjust to match your `app.py` routes.

### Health Check
```http
GET /health
```
**Response (200):**
```json
{"status":"ok"}
```

### Example POST
```http
POST /api/example
Content-Type: application/json

{"message":"hello"}
```
**Response (200):**
```json
{"message":"hello"}
```

---

## 🐳 Docker Setup

### Option A — Build locally
#### 1. Build the image
```bash
docker build -t flask-app .
```

#### 2. Run the container
```bash
docker run -p 5000:5000 flask-app
```

### Option B — Docker Hub (Pull & Run)
> Replace `<dockerhub-username>` and `<image-name>` with your published image.

```bash
docker pull <dockerhub-username>/<image-name>:latest
```

```bash
docker run --rm -p 5000:5000 <dockerhub-username>/<image-name>:latest
```

---

## ⚙️ Environment Variables
If your app needs configuration at runtime, prefer environment variables over hardcoding values.

| Variable | Required | Default | Description |
|---|---:|---|---|
| `FLASK_ENV` | No | `production` | Flask environment mode |
| `FLASK_APP` | No | `app.py` | Flask entrypoint |
| `PORT` | No | `5000` | Port the server listens on |

**Example:**
```bash
docker run -p 5000:5000 \
  -e FLASK_ENV=production \
  -e PORT=5000 \
  flask-app
```

---

## 📦 Requirements
- Python 3.8
- Flask

Install dependencies:
```bash
pip install -r requirements.txt
```

---

## 📂 Project Structure
```text
.
├── app.py
├── Dockerfile
├── requirements.txt
├── templates/
└── static/
```

---

## 🖼️ Screenshots
<img width="1494" height="785" alt="image" src="https://github.com/user-attachments/assets/9cd977a8-08cf-4802-ad5d-50cfe0f258c2" />


---

## 🔥 Key Learnings
- Dockerizing Flask apps
- Writing efficient Dockerfiles
- Managing dependencies in containers
- Image optimization

---

## 🛣️ Future Improvements
- Add a `/health` endpoint and basic healthcheck in the Dockerfile
- Add structured logging (JSON) and request tracing
- Add unit tests + CI pipeline (GitHub Actions)
- Add production WSGI server (e.g., Gunicorn) and configuration

---

## 🧑‍💻 Author
**Yash Jajoria**
