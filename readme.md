# Flask + Redis Visit Counter 🐳

A hands-on Docker Compose project that spins up two containers — Flask and Redis — to count and display page visits in real time.

---

## 📌 What It Does

Every time you visit the page, Flask receives the request, Redis increments the counter, and the updated count is displayed in the browser.

```
This page has been visited 5 times.
```

---

## 🏗️ Architecture

```
Browser
   │
   ▼
Flask App (port 5000)
   │  reads/writes hit count
   ▼
Redis (internal, port 6379)
```

| Service | Image | Role |
|--------|-------|------|
| `flask` | Built from Dockerfile | Handles HTTP requests, displays count |
| `redis` | `redis:latest` (Docker Hub) | Stores and increments visit count |

Docker Compose manages both containers, their networking, and config — all in one `docker-compose.yml`.

---

## 🚀 How to Run

**Prerequisites:** Docker + Docker Compose plugin installed on your machine.

```bash
# Clone the repo
git clone https://github.com/Siddhesh-07/flask-redis-docker-compose.git
cd flask-redis-docker-compose

# Start containers in detached mode
docker compose up -d
```

Then open your browser:

```
http://<your-ec2-public-ip>:5000
```

Refresh the page and watch the count go up.

---

## 🛠️ Useful Commands

```bash
docker compose ps       # Check running containers
docker compose logs     # View container logs
docker compose stop     # Stop containers
docker compose down     # Stop and remove containers + network
```

---

## 💡 What I Learned

- Writing `docker-compose.yml` from scratch
- Running multi-container apps with a single command
- Difference between building a custom image (Flask) vs pulling an official one (Redis)
- How Compose automatically handles container networking
- Detached mode and container lifecycle management

---

## 🗂️ Project Structure

```
flask-redis-docker-compose/
├── app.py                  # Flask application
├── requirements.txt        # Python dependencies
├── Dockerfile              # Builds the Flask image
├── docker-compose.yml      # Defines and runs both services
└── README.md
```

---

> **Tech Stack:** Python · Flask · Redis · Docker · Docker Compose · AWS EC2
