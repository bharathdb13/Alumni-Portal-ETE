# Alumni-Portal-ETE


Here’s a **more structured and well-formatted README** for your project, keeping all the details from your original file but making it cleaner, more navigable, and developer-friendly.

---

# 🎓 AlmaniPortal - Alumni Management System

A comprehensive full-stack web application for managing alumni networks, built for the **Electronics and Telecommunication Department (ETE)** at **Dr. Ambedkar Institute of Technology, Bengaluru**.

---

## 📚 Table of Contents

1. [Architecture](#-architecture)
2. [Features](#-features)
3. [Prerequisites](#-prerequisites)
4. [Installation & Setup](#-installation--setup)
5. [Running the Application](#-running-the-application)
6. [Testing](#-testing)
7. [Production Deployment](#-production-deployment)
8. [Configuration](#-configuration)
9. [Monitoring & Maintenance](#-monitoring--maintenance)
10. [Troubleshooting](#-troubleshooting)
11. [Contributing](#-contributing)
12. [License](#-license)
13. [Acknowledgments](#-acknowledgments)
14. [Support](#-support)

---

## 🏗 Architecture

* **Frontend**: Next.js 14 + TypeScript + Tailwind CSS
* **Backend**: Go + Fiber Framework
* **Database**: MongoDB
* **Real-time**: WebSocket connections
* **Authentication**: JWT tokens + Email OTP
* **File Storage**: Local storage with upload validation

---

## 🚀 Features

### 👥 Multi-Role System

* **Students**: Post projects, apply for jobs, network with alumni
* **Alumni**: Post job opportunities, mentor students, share experiences
* **Faculty**: Manage events, moderate content, guide students
* **Admin**: System administration, user management, analytics

### 🔧 Core Functionality

* Real-time Messaging (WebSocket-powered chat)
* Project Showcase for students
* Job Portal for alumni postings
* Event Management for faculty
* Event Gallery & Achievements
* Automated Email Notifications

---

## 📋 Prerequisites

Ensure you have the following installed:

* **Go** 1.21+
* **Node.js** 18+ with npm/yarn
* **MongoDB** 7.0+ (local or remote)
* **SMTP credentials** (Gmail recommended)

---

## 🛠 Installation & Setup

### 1️⃣ Clone Repository

```bash
git clone <repository-url>
cd almaniportal
```

### 2️⃣ Backend Setup

```bash
cd backend
go mod tidy
cp .env.example .env
nano .env
```

Set environment variables:

```env
MONGODB_URI=mongodb://localhost:27017/alumni_ete_new
DB_NAME=alumni_ete_new
JWT_SECRET=change-this-in-production
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USERNAME=your-email@gmail.com
SMTP_PASSWORD=your-app-password
FRONTEND_URL=http://localhost:3000
```

### 3️⃣ Frontend Setup

```bash
cd frontend
npm install
cp .env.example .env.local
nano .env.local
```

Frontend variables:

```env
NEXT_PUBLIC_API_URL=http://localhost:8080/api/v1
NEXT_PUBLIC_WS_URL=ws://localhost:8080/ws
```

### 4️⃣ Database Setup

```bash
mongod
cd backend
go run scripts/setup_db.go
```

---

## 🚀 Running the Application

### **Option 1: Manual (Development)**

```bash
# Terminal 1 - MongoDB
mongod

# Terminal 2 - Backend
cd backend
go run main.go

# Terminal 3 - Frontend
cd frontend
npm run dev
```

**Access:**

* Frontend → [http://localhost:3000](http://localhost:3000)
* Backend API → [http://localhost:8080](http://localhost:8080)

### **Option 2: Docker Compose (Recommended)**

```bash
docker-compose up --build
# or run in background
docker-compose up -d --build
```

---

## 🧪 Testing

### Backend

```bash
cd backend
go test ./internal/tests/... -v
```

### Frontend

```bash
cd frontend
npm test
```

---

## 📦 Production Deployment

### Build Docker Images

```bash
cd backend
docker build -t almaniportal-backend:latest .

cd ../frontend
docker build -t almaniportal-frontend:latest .
```

### Deploy with Production Docker Compose

```bash
cp .env.example .env.prod
nano .env.prod
docker-compose -f docker-compose.prod.yml --env-file .env.prod up -d
```

---

## 🔧 Configuration

### SMTP Setup (Gmail)

1. Enable **2FA** in Gmail
2. Generate **App Password** under Google Account → Security → App passwords
3. Use the generated password in `SMTP_PASSWORD`

### MongoDB Production Tips

* Use MongoDB Atlas or Replica Sets
* Create proper indexes
* Schedule backups

---

## 📊 Monitoring & Maintenance

**Health Checks**

```bash
curl http://localhost:8080/health
curl http://localhost:8080/api/v1/health/db
```

**Logs**

```bash
docker-compose logs -f backend
docker-compose logs -f frontend
```

**Backup**

```bash
docker exec almaniportal-mongodb-prod mongodump --out /backup
```

---

If you want, I can also prepare a **developer quick-start guide** as a separate `CONTRIBUTING.md` so onboarding is faster. That would make this README shorter and even more structured.
