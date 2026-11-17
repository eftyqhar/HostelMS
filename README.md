# HostelMS — College Hostel Management System (Full-Stack)

A modern, full-stack college hostel management system built for **X Institute**, featuring dual portals for **Admin Management** and the **Student Portal** with a **FastAPI + SQLite** backend and **React 19 + TypeScript + Tailwind CSS v4** frontend.

---

## 🏗️ Architecture

```
HostelMS/
├── server/                     # FastAPI Backend (Python)
│   ├── database.py             # SQLite schema and automatic initial seed
│   ├── models.py               # Pydantic data validation models
│   ├── main.py                 # REST API endpoints & CORS middleware
│   ├── hostel.db               # SQLite database file (auto-generated)
│   └── requirements.txt        # Backend dependencies
├── src/                        # React Frontend (TypeScript)
│   ├── components/
│   │   ├── admin/              # Admin dashboard widgets & layouts
│   │   ├── student/            # Student portal widgets & layouts
│   │   ├── home/               # Landing page & navigation
│   │   ├── auth/               # Authentication & registration forms
│   │   ├── common/             # Header, Sidebar, Modal, Toast
│   │   └── modals/             # Action dialogs (Add Student, Assign Room, Pay, etc.)
│   ├── context/
│   │   └── HostelContext.tsx   # Global state synced with FastAPI backend & localStorage
│   ├── services/
│   │   └── api.ts              # REST client for backend communication
│   ├── types/
│   │   └── index.ts            # TypeScript interfaces
│   ├── App.tsx                 # Main layout & role orchestrator
│   └── index.css               # Tailwind CSS v4 styling
├── package.json
└── README.md
```

---

## 📋 Prerequisites

Before installing, ensure you have the following installed on your system:

- **Node.js**: v18.0.0 or higher (v20+ LTS recommended)
- **npm**: v9.0.0 or higher
- **Python**: v3.10, v3.11, v3.12, or v3.13
- **Git**

---

## 📥 Installation Guide

### 1. Clone the Repository

```bash
git clone https://github.com/eftyqhar/HostelMS.git
cd HostelMS
```

---

### 2. Backend Setup (FastAPI)

1. **Create a Python Virtual Environment**:

   - **Windows (PowerShell / Command Prompt)**:
     ```powershell
     python -m venv server\venv
     ```
   - **macOS / Linux**:
     ```bash
     python3 -m venv server/venv
     ```

2. **Activate the Virtual Environment**:

   - **Windows (PowerShell)**:
     ```powershell
     .\server\venv\Scripts\Activate.ps1
     ```
     *(If script execution is disabled on your system, run: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`)*
   - **Windows (Command Prompt)**:
     ```cmd
     server\venv\Scripts\activate.bat
     ```
   - **macOS / Linux**:
     ```bash
     source server/venv/bin/activate
     ```

3. **Install Backend Dependencies**:

   ```bash
   pip install -r server/requirements.txt
   ```

4. **Database Note**:
   The SQLite database (`server/hostel.db`) is automatically initialized and seeded with demo rooms, students, meals, and admin accounts upon starting the server. No manual migrations are required for local development.

---

### 3. Frontend Setup (React + Vite)

In the project root directory, install all JavaScript/TypeScript dependencies:

```bash
npm install
```

---

## ⚡ Running the Application

For full functionality, run both the backend and frontend servers simultaneously in separate terminal windows.

### Terminal 1: Run Backend (FastAPI on Port 8000)

Using npm:
```powershell
npm run server
```

Or directly using Python/Uvicorn:
- **Windows**:
  ```powershell
  .\server\venv\Scripts\uvicorn server.main:app --reload --port 8000
  ```
- **macOS / Linux**:
  ```bash
  uvicorn server.main:app --reload --port 8000
  ```

* Backend API: [http://127.0.0.1:8000](http://127.0.0.1:8000)
* Interactive Swagger Docs: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
* ReDoc API Docs: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

---

### Terminal 2: Run Frontend (React + Vite)

```bash
npm run dev
```

* Frontend Web App: [http://localhost:5173](http://localhost:5173)

---

## 🔑 Demo Access Credentials

| Role | Identifier / Email | Password | Access Level |
|---|---|---|---|
| **Admin / Warden** | `admin@spi.edu.bd` (or `admin`) | `admin123` | Full administrative control |
| **Student** | `rahim.cse@spi.edu.bd` (or `1021`) | `student123` | Personal hostel dashboard |

---

## 📡 REST API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/health` | Service health status |
| `GET` | `/api/stats` | Top-level KPI counts and occupancy percentages |
| `GET` | `/api/students` | Get all students (supports sorting/filtering) |
| `POST` | `/api/students` | Register new student admission |
| `GET` | `/api/rooms` | Get rooms layout with bed occupancy mapping |
| `POST` | `/api/rooms/assign` | Assign student to room & bed slot |
| `GET` | `/api/complaints` | Get complaints (all or filtered by student) |
| `POST` | `/api/complaints` | Submit a maintenance or room repair complaint |
| `PATCH`| `/api/complaints/{id}/status` | Advance status (`Pending` ➔ `In Progress` ➔ `Resolved`) |
| `GET` | `/api/payments` | Get payment records |
| `POST` | `/api/payments` | Record fee payment with transaction ID |
| `GET` | `/api/meals` | Today's meal menu & student attendance |
| `PATCH`| `/api/meals/{type}/toggle` | Toggle breakfast/lunch/dinner checkmark |
| `GET` | `/api/visitors` | List of today's visitors and gate passes |
| `POST` | `/api/visitors` | Issue guest visitor pass |
| `GET` | `/api/attendance` | Night roll-call attendance history |
| `GET` | `/api/notices` | Official hostel announcements |
| `GET` | `/api/activities` | Real-time audit activity feed |

---

## 🛠️ Building for Production

To create an optimized production build of the frontend:

```bash
npm run build
```

The compiled assets will be output to the `dist/` directory.

To preview the production build locally:

```bash
npm run preview
```

---

## 🎨 Dual Portal Views

1. **Admin Portal**: Full control over student admissions, room layouts, bed allocations, complaint tracking, payment collection, and visitors.
2. **Student Portal (Rahim Ahmed)**: Personalized dashboard displaying assigned room, bed number, room photo, payment history with printable PDF receipts, interactive meal checklist, and gate pass requests.

---

## 📄 License

This project is licensed under the MIT License.
