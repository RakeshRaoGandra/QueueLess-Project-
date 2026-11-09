# QueueLess — Smart Real-Time Hospital Queue Management System

QueueLess is a real-time hospital queue and appointment management platform designed to reduce waiting times and optimize patient flow.

> 📖 **New to the project?** Read our beginner-friendly [Super Easy Step-by-Step Guide (VS Code & Docker)](./HOW_TO_RUN_GUIDE.md) to get running in 1 minute!

---

## 🏛️ Architecture (Pure React & Node.js)

- **Frontend**: Next.js 15 (App Router), React 18, Tailwind CSS, Zustand, TanStack Query.
- **Backend**: Node.js 20, Express, Native WebSockets (`ws`), JSON Web Tokens (JWT), bcrypt.
- **Data Persistence**: File-backed JSON data store (`data.json`) with auto-seeding and relational integrity.
- **Deployment**: Docker & Docker Compose (minimal Alpine/Slim containers).

---

## ✨ Features

- **Real-Time Updates**: Live queue synchronization across patient, doctor, and receptionist screens using WebSockets (`ws://localhost:8000/ws/queue/:room`).
- **Priority Management**: Emergency (1), Serious (2), and Normal (3) triage levels with priority override audits.
- **Role-Based Access Control (RBAC)**: Secure JWT verification with dedicated dashboards for Admin, Doctor, Receptionist, and Patient.
- **Wait Time Estimation**: Dynamic calculation based on active waiting tokens.
- **DevOps Ready**: Pre-configured Docker Compose with container healthchecks.

---

## 🚀 Getting Started

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Node.js](https://nodejs.org/) (v18+)

---

### Running with Docker Desktop (Recommended)

1. Ensure Docker Desktop is running.
2. In the project root, run:
   ```bash
   docker compose up --build
   ```
3. Access the applications:
   - **Hospital Website**: [http://localhost:3000](http://localhost:3000)
   - **Backend API**: [http://localhost:8000](http://localhost:8000)
   - **Health Check**: [http://localhost:8000/health](http://localhost:8000/health)

---

### Running Locally (Without Docker)

#### 1. Backend (Node.js & Express)
```bash
cd apps/api
npm install
npm run seed     # Seeds default users & departments
npm start        # Starts server on http://localhost:8000
```

#### 2. Frontend (Next.js & React)
```bash
cd apps/web
npm install
npm run dev      # Starts Next.js on http://localhost:3000
```

---

## 🧪 Automated Testing

Run the full end-to-end integration and API test suite:

```bash
npm test --prefix apps/api
```

This verifies:
1. Root & Health check endpoints (`/`, `/health`).
2. Authentication & JWT issuing (`/api/v1/auth/login`).
3. User registration & role permissions (`/api/v1/auth/register`).
4. Department list with live waiting counts (`/api/v1/departments`).
5. Queue token generation (`/api/v1/queue/create-token`).
6. Emergency priority sorting in live queue (`/api/v1/queue/live/:id`).
7. Doctor calling next patient (`/api/v1/queue/call-next`).
8. Consultation completion (`/api/v1/queue/complete/:id`).
9. Receptionist priority override & audit logging (`/api/v1/queue/override-priority`).

---

## 🔑 Default Credentials

| Role | Email | Password | Access URL |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@queueless.com` | `Admin@123` | [http://localhost:3000/admin](http://localhost:3000/admin) |
| **Doctor** | `doctor@queueless.com` | `doctor123` | [http://localhost:3000/doctor](http://localhost:3000/doctor) |
| **Receptionist** | `receptionist@queueless.com` | `recep123` | [http://localhost:3000/receptionist](http://localhost:3000/receptionist) |
| **Patient** | `patient@queueless.com` | `patient123` | [http://localhost:3000/patient](http://localhost:3000/patient) |

**Admin Secret Key for New Registrations:** `super-secret-admin-key`
