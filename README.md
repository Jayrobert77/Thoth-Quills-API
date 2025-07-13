# Thoth's Quill API

A dual-purpose AI Codex Builder & Manuscript Engine.  
**Backend:** FastAPI + OpenAI | **Frontend:** (Vercel/Next.js recommended)

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Project Structure](#project-structure)
3. [Setup and Installation](#setup-and-installation)
4. [Environment Variables](#environment-variables)
5. [API Endpoints](#api-endpoints)
6. [Deployment Options](#deployment-options)
7. [Troubleshooting](#troubleshooting)

---

## Prerequisites

- Python 3.8+
- OpenAI API Key ([get one here](https://platform.openai.com/account/api-keys))
- `fastapi`, `uvicorn`, `openai`, `python-dotenv` (see below for install)
- Familiarity with API testing tools (Postman, curl, etc.)

---

## Project Structure

```plaintext
thoths-quill/
├── app/
│   ├── main.py
│   ├── ai_config.py
│   ├── models.py
│   ├── routes/
│   │   ├── codegen.py
│   │   └── writing.py
│   └── utils/
│       └── formatter.py
├── .env
├── requirements.txt
└── README.md
```

---

## Setup and Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-repo/thoths-quill.git
   cd thoths-quill
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Linux/Mac
   venv\Scripts\activate     # On Windows
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

---

## Environment Variables

1. **Create a `.env` file** in the root directory:
   ```env
   OPENAI_API_KEY=sk-xxxxxxx-your-real-key-here
   ```

---

## API Endpoints

### 1. Generate Starter Code Project (Alchemist)
- **POST** `/code/invoke-project-alchemist`
- **Body:**
  ```json
  {
    "prompt": "Your project idea",
    "style": "Your preferred style",
    "context": "Any additional context"
  }
  ```

### 2. Generate Manuscript Outline & Sample Chapter (Scribe)
- **POST** `/scribe/summon-manuscript-scribe`
- **Body:**
  ```json
  {
    "prompt": "Your book idea",
    "style": "Your preferred style",
    "narrative_arc": "Desired narrative arc"
  }
  ```

### 3. Generate a Specific Chapter
- **POST** `/scribe/generate-chapter`
- **Body:**
  ```json
  {
    "chapter_summary": "Summary of the chapter",
    "previous_chapters": ["List of previous chapters"],
    "style": "Your preferred style"
  }
  ```

### 4. Discern Creation Path
- **POST** `/discern-creation-path`
- **Body:**
  ```json
  {
    "user_goal": "Describe your goal to determine if it's for Code or Writing"
  }
  ```

---

## Deployment Options

### 1. Render.com (Backend)
- Create an account at [Render.com](https://render.com)
- New Web Service > Python
- Link your GitHub repo
- **Start command:**  
  `uvicorn app.main:app --host 0.0.0.0 --port 10000`
- Set `OPENAI_API_KEY` as environment variable
- Deploy!

### 2. Fly.io (Alternative Backend)
- Create an account at [Fly.io](https://fly.io)
- `fly launch`
- Edit `fly.toml` to run `uvicorn app.main:app --host 0.0.0.0 --port 8080`
- `fly deploy`

### 3. Vercel (Frontend)
- [vercel.com](https://vercel.com) > Import Next.js/React frontend
- Deploy

---

## Troubleshooting

- **API Key Issues:**  
  Ensure `OPENAI_API_KEY` is set in `.env` or render/fly env vars.
- **Deployment Errors:**  
  Check platform logs for Python, dependency, or API errors.
- **Endpoint Errors:**  
  Use `/docs` (Swagger UI) or Postman/curl for request tests.

---

## Quickstart (Local)
```bash
uvicorn app.main:app --reload
# Visit: http://127.0.0.1:8000/docs
```

---

## Credits

- Named for Thoth (wisdom) & Seshat (memory, writing)
- Powered by OpenAI GPT-4o

---
