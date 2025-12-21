# Smart HR & Employee Management System

A modern, full‑stack Smart HR and Employee Management System built with **FastAPI** (backend), **PostgreSQL** (database), and **React (Vite + Tailwind CSS)** (frontend). The project includes AI‑powered features (OpenAI integration), Dockerized infrastructure, and production‑ready patterns such as Alembic migrations and modular code organization.

---

## 🚀 Project Status

**Backend (FastAPI + PostgreSQL)** ✅

* Core setup files: `main.py`, `config.py`, `database.py`, `auth.py`
* Database models: `User`, `Employee`, `Attendance`, `Leave`, `Recruitment`, `Payroll`, `Performance`
* Pydantic schemas for request/response validation
* Complete REST API routes for all modules
* AI service integration (OpenAI)
* Utility functions: email, PDF generation (salary slips, reports), helpers
* Alembic configuration for database migrations

**Frontend (React.js)** ✅

* Vite + Tailwind CSS setup
* Authentication context and protected routes
* Common components: `Navbar`, `Sidebar`, `Modal`, `Table`, etc.
* Pages: `Login`, `Dashboard`, `Employees`, `Attendance`, `Leave`, `Recruitment`, `Payroll`, `Performance`, `Reports`, `Settings`
* API service integrations and custom hooks: `useAuth`, `useEmployees`, `useAI`
* AI components: `Chatbot`, `Predictive Analytics`, `Sentiment Analysis`, `Smart Scheduler`
* Validators and utility helpers

**Infrastructure** ✅

* `docker-compose.yml` (frontend, backend, postgres)
* `Dockerfile` for backend and frontend
* `.gitignore` included
* This README with setup instructions

---

## 🎯 Key Features

### Core HR Features

* **Employee Management** — Full CRUD with departments, roles, and employee profiles
* **Attendance Tracking** — Check-in/out, calendar view, daily/period reports
* **Leave Management** — Request, approve/reject, multiple leave types and balances
* **Recruitment** — Job postings, candidate pipeline, resume uploads, interview scheduling
* **Payroll** — Salary management, payroll cycles, PDF salary slips
* **Performance** — Reviews, goals, and appraisal workflows
* **Reports & Analytics** — Dashboards and exportable reports

### AI‑Powered Features

* **AI Chatbot** — HR assistant for FAQs and common tasks
* **Resume Scanner** — AI‑assisted candidate matching and ranking
* **Predictive Analytics** — Turnover risk and performance forecasting
* **Sentiment Analysis** — Analyze employee feedback and survey responses
* **Smart Scheduler** — AI‑optimized shift and meeting scheduling

---

## 🛠 Tech Stack

* Backend: FastAPI, Pydantic, SQLAlchemy
* Database: PostgreSQL
* Migrations: Alembic
* Frontend: React (Vite), Tailwind CSS
* AI: OpenAI (ChatGPT / embeddings / custom prompts)
* DevOps: Docker, Docker Compose
* Charts: Recharts (frontend)

---

## 📦 Quick Start

### Option 1 — Docker (recommended)

```bash
# from project root
git clone <repo-url> smart-hr
cd smart-hr
# create .env files for backend and frontend (see .env.example)
docker-compose up -d --build
```

* Backend available at: `http://localhost:8000`
* Frontend available at: `http://localhost:3000`
* API docs: `http://localhost:8000/docs`

### Option 2 — Manual (local development)

#### Backend (Linux / macOS)

```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
# configure .env file (copy .env.example -> .env)
uvicorn app.main:app --reload --port 8000
```

#### Backend (Windows - PowerShell)

```powershell
cd backend
python -m venv venv
venv\Scripts\Activate.ps1
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

#### Frontend

```bash
cd frontend
npm install
npm run dev
# opens at http://localhost:3000
```

---

## ⚙️ Database & Migrations

1. Make sure PostgreSQL is running on port `5432` (or update `.env` accordingly).
2. Create the database (example name: `smarthr_db`).
3. Run Alembic migrations:

```bash
# from backend directory
alembic upgrade head
```

---

## 🔑 Environment Variables

Create `.env` files for the backend and frontend (examples included in repo). Important variables:

**Backend `.env`** (example)

```env
DATABASE_URL=postgresql+psycopg2://user:password@postgres:5432/smarthr_db
SECRET_KEY=your-secret-key
OPENAI_API_KEY=sk-xxxxxx
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USERNAME=your-email@example.com
SMTP_PASSWORD=your-email-password
FRONTEND_URL=http://localhost:3000
```

**Frontend `.env`** (example)

```env
VITE_API_URL=http://localhost:8000/api
VITE_OPENAI_KEY=sk-xxxxxx # if needed for client-side features
```

> ⚠️ Do not commit `.env` files with real credentials to version control.

---

## 🔐 Default Credentials (Local Dev)

* **Email:** `admin@smarthr.com`
* **Password:** `Admin@123`

Use these to sign in locally or create your own admin user via seed script or directly in the database.

---

## 📚 API Documentation

When the backend is running, interactive API docs are available at:

```
http://localhost:8000/docs
```

---

## 🧭 Project Structure (high level)

```
smart-hr/
├─ backend/
│  ├─ app/
│  │  ├─ main.py
│  │  ├─ config.py
│  │  ├─ database.py
│  │  ├─ models/    # SQLAlchemy models
│  │  ├─ schemas/   # Pydantic schemas
│  │  ├─ routes/    # routers for employees, auth, payroll, etc.
│  │  ├─ services/  # AI service, email, payroll helpers
│  │  ├─ utils/     # pdf generator, validators
│  │  └─ alembic/
│  └─ requirements.txt

├─ frontend/
│  ├─ src/
│  │  ├─ components/
│  │  ├─ pages/
│  │  ├─ context/   # auth context
│  │  ├─ hooks/     # useAuth, useEmployees, useAI
│  │  ├─ services/  # api service wrappers
│  │  └─ styles/
│  └─ package.json

├─ docker-compose.yml
├─ Dockerfile.backend
├─ Dockerfile.frontend
└─ README.md
```

---

## 🎨 Design & UX

* Responsive UI using Tailwind CSS
* Gradient accents and smooth micro‑animations
* Card‑based layout, consistent spacing, and clean typography
* Interactive charts (Recharts) for dashboards
* Toast notifications and loading/error states

---

## 🧪 Testing & Quality

* Follow repository linting rules (ESLint, Prettier, Black/Flake8 for Python if configured)
* Add unit/integration tests where relevant (not included by default)

---

## 🔄 Next Steps / Checklist

1. Set up PostgreSQL and create the database
2. Update `.env` files with real credentials
3. Install dependencies for frontend and backend
4. Run migrations: `alembic upgrade head`
5. Start services (Docker or manual)
6. Verify `http://localhost:8000/docs` for APIs and `http://localhost:3000` for the UI
7. Configure CI/CD, backups, and secret management for production

---

## ❗ Notes & Disclaimers

* The project is production‑grade in structure and follows modular best practices, but **you must** review and secure secrets, CORS policies, authentication flows, and rate limiting before deploying to production.
* AI features depend on your OpenAI API key — usage may incur costs. Tune prompts and monitor usage.
* This README was generated automatically; please double‑check instructions and update environment examples to match your deployment environment.

---

## 🙋 Need Changes?

If you want a different tone (shorter, developer‑focused, or end‑user guide), or want this exported as `README.md` file in the repo, tell me which format and I'll generate it.

---

*All files are ready to use and follow best practices for modular, maintainable, and scalable web applications.*

*Generated with assistance from an AI. Please verify configuration and secrets before production deploy.*
