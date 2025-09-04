# 🚀 Reverse Proxy Multi-Container Docker Setup

This project demonstrates a **Production-style Multi-Container Setup** using **Docker Compose** with:
- ✅ Frontend served by **Nginx**
- ✅ Backend API built with **Flask (Python)**
- ✅ **Reverse Proxy** to serve both Frontend and Backend on a single port (`:80`)

---

## 📂 Project Structure
reverse-proxy-app/
├── backend/
│ ├── app.py
│ ├── Dockerfile
│ └── requirements.txt
├── frontend/
│ ├── index.html
│ └── Dockerfile
├── nginx/
│ ├── nginx.conf
│ └── Dockerfile
└── docker-compose.yml

---

## 🔹 Services
	| Service      | Port | Description                    |
	|--------------|------|--------------------------------|
	| **Frontend** | 80   | Static HTML site via Nginx     |
	| **Backend**  | 5000 | Flask API (proxied via Nginx)  |
	| **Nginx**    | 80   | Reverse Proxy for Frontend/API |

---

## ⚙️ How It Works
- `Nginx` acts as a **reverse proxy**:
  - `/` → Frontend Container
  - `/api` → Backend Container
- All traffic goes through a **single port (80)**, making it production-friendly.

---

## 🚀 Getting Started

### 1️⃣  Clone the Repository
	git clone https://github.com/<your-username>/reverse-proxy-app.git
	cd reverse-proxy-app

### 2️⃣  Build & Run
	docker-compose up -d --build

### 3️⃣  Test in Browser
	Frontend: http://<EC2-IP>/
	Backend (API): http://<EC2-IP>/api

🔥 Stopping the Containers
	docker-compose down

