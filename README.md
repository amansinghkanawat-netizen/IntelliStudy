# IntelliStudy – Smart Study Generator Agent

> **Your Personal AI Learning Companion**  
> Powered by IBM Granite AI via IBM watsonx.ai

---

## 🚀 Overview

IntelliStudy is a full-stack AI-powered EdTech platform that transforms student study materials into intelligent learning resources. Upload a PDF, DOCX, TXT, or textbook image — and IntelliStudy generates summaries, flashcards, quizzes, concept maps, and personalised study plans using IBM Granite foundation models.

## ✨ Features

| Feature | Description |
|---|---|
| 📄 AI Study Generator | Upload documents → AI generates summaries, notes, questions |
| 🃏 Smart Flashcards | Auto-generated with spaced repetition & mastery tracking |
| 📝 Quiz Generator | MCQ, True/False quizzes with scoring & explanations |
| 🤖 AI Personal Tutor | RAG-powered chatbot from your uploaded materials |
| 🗺️ Concept Maps | Visual topic relationship maps |
| 📅 Study Planner | AI-generated personalised timetables |
| 📊 Predictive Analytics | Performance analysis & weak-topic detection |
| 🛡️ Admin Dashboard | User management & platform analytics |

## 🛠️ Tech Stack

- **Frontend:** React 18 · Tailwind CSS · Framer Motion · Recharts · Lucide Icons
- **Backend:** Python 3.11+ · FastAPI · SQLAlchemy · Alembic
- **AI:** IBM Granite (via IBM watsonx.ai) · RAG pipeline · Text embeddings
- **Database:** PostgreSQL (production) / SQLite (development)
- **Storage:** IBM Cloud Object Storage / Local filesystem (dev)

---

## 📦 Installation

### Prerequisites
- Node.js ≥ 18
- Python ≥ 3.11
- (Optional) PostgreSQL for production

### 1. Clone & setup environment

```bash
# Copy environment template
cp .env.example .env
# Edit .env with your IBM watsonx.ai credentials (or leave blank for Demo mode)
```

### 2. Frontend setup

```bash
cd frontend
npm install
```

### 3. Backend setup

```bash
cd backend
py -m pip install -r requirements.txt
```

> **Note:** `psycopg2-binary` requires PostgreSQL client. If you only need SQLite for development, you can skip it or use `psycopg2` only when deploying.

---

## ▶️ Running the Application

### Start the Backend

```bash
# From project root
py -m uvicorn backend.main:app --reload --port 8000
```

The API will be available at: http://localhost:8000  
Interactive API docs: http://localhost:8000/docs

### Start the Frontend

```bash
cd frontend
npm run dev
```

The app will be available at: http://localhost:3000

---

## 🔑 IBM watsonx.ai Configuration

1. Create an IBM Cloud account: https://cloud.ibm.com
2. Create a watsonx.ai project: https://dataplatform.cloud.ibm.com
3. Generate an API key: https://cloud.ibm.com/iam/apikeys
4. Add to `.env`:

```env
WATSONX_API_KEY=your_api_key_here
WATSONX_PROJECT_ID=your_project_id_here
WATSONX_URL=https://us-south.ml.cloud.ibm.com
```

**Demo Mode:** If credentials are not configured, the platform runs in clearly labelled DEMO mode with sample AI responses. All UI features remain functional.

---

## 📂 Project Structure

```
IntelliStudy/
├── frontend/                   # React frontend
│   ├── src/
│   │   ├── components/         # Reusable UI components
│   │   │   ├── layout/         # Navbar, Footer
│   │   │   └── dashboard/      # Sidebar, Topbar
│   │   ├── pages/              # Page components
│   │   ├── layouts/            # Page layout wrappers
│   │   ├── context/            # React context (Auth)
│   │   ├── services/           # API client
│   │   └── index.css           # Global styles + Tailwind
│   └── package.json
│
├── backend/                    # FastAPI backend
│   ├── main.py                 # App entry point
│   ├── config.py               # Settings (pydantic-settings)
│   ├── database/               # DB engine + session
│   ├── models/                 # SQLAlchemy ORM models
│   ├── routes/                 # API route handlers
│   ├── services/               # Business logic
│   │   ├── auth_service.py     # JWT + password hashing
│   │   └── granite_service.py  # IBM Granite integration
│   ├── agents/                 # Multi-agent AI (Phase 5)
│   ├── rag/                    # RAG pipeline (Phase 3)
│   └── requirements.txt
│
├── storage/                    # File uploads + vector store
├── tests/                      # Test suites
├── docs/                       # Documentation
├── .env.example                # Environment template
├── Dockerfile
└── README.md
```

---

## 🔐 Security

- Passwords hashed with bcrypt (passlib)
- JWT authentication (python-jose)
- File type validation (allowlist-based)
- File size limits (25MB default)
- User data isolation (all queries scoped to user_id)
- Environment variables for all secrets (never hardcoded)

---

## 🗺️ Development Roadmap

- [x] **Phase 1** — Frontend UI, Auth, Dashboards
- [ ] **Phase 2** — Backend APIs, Database, File Upload, OCR
- [ ] **Phase 3** — IBM watsonx.ai, Embeddings, RAG Pipeline
- [ ] **Phase 4** — Study Generator, Tutor, Flashcards, Quiz, Concept Maps
- [ ] **Phase 5** — Study Planner, Multi-Agent, Analytics
- [ ] **Phase 6** — Testing, Security, IBM Cloud Deployment

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

*Built with ❤️ for the IBM Hackathon · IntelliStudy – Study Smarter. Learn Faster. Achieve More.*
