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
- OpenAI API Key ([get one here](hThoth render 

**Deploying Thoth's Quill API to Render.com (Backend)**
=====================================================

**Step-by-Step Deployment Guide**
-------------------------------

### **Prerequisites**
* **Render.com Account**: Create one if you haven't already ([Render.com](https://render.com/))
* **GitHub Repository**: Ensure your Thoth's Quill API repository is publicly accessible on GitHub
* **OpenAI API Key**: Verify your key is correctly set in your `.env` file

### **Deployment Steps**
#### **1. Create a New Render Web Service**
* **Login to Render.com**: Navigate to [Render.com](https://render.com/) and log in to your account
* **Click on "New+"**: Located at the top right corner of the dashboard
* **Select "Web Service"**: From the dropdown menu

#### **2. Configure Your Web Service**
* **Service Name**: Enter a name for your service (e.g., "Thoth's Quill API")
* **Environment**: Select "Python" as the environment
* **Branch**: Choose the branch you want to deploy from your GitHub repository (typically "main")
* **Root Directory**: Leave this as the default (your repository's root)
* **Build Command**: Enter `pip install -r requirements.txt`
* **Start Command**: Enter `uvicorn app.main:app --reload`

#### **3. Link Your GitHub Repository**
* **Repository**: Select "GitHub" and authorize Render to access your GitHub account
* **Repository Name**: Choose your Thoth's Quill API repository from the list

#### **4. Configure Environment Variables**
* **Environment Variables**: Click on "New Environment Variable"
* **Key**: Enter `OPENAI_API_KEY`
* **Value**: Paste your actual OpenAI API Key (ensure it's correct and secure)

#### **5. Finalize and Deploy**
* **Create Web Service**: Review your settings, then click "Create Web Service"
* **Deployment**: Render will now clone your repository, install dependencies, and deploy your service. **Wait for the deployment to complete**.

#### **6. Verify Your Deployment**
* **Service Dashboard**: Once deployed, navigate to your service's dashboard on Render
* **Logs**: Check the logs for any errors or issues
* **Endpoint**: Your API should now be accessible via the provided URL (e.g., `https://thoths-quill.onrender.com`)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
* **Test Your API**: Use tools like Postman or `curl` to test your API endpoints

**Example API Endpoint URL**:
```plaintext
https://thoths-quill.onrender.com/code/invoke-project-alchemist
```
**Test with `curl`**:
```bash
curl -X POST \
  https://thoths-quill.onrender.com/code/invoke-project-alchemist \
  -H 'Content-Type: application/json' \
  -d '{"prompt": "Your project idea", "style": "Your preferred style", "context": "Any additional context"}'
```

**Deployment Status**: **IN PROGRESS** (awaiting your confirmation of successful deployment)

**Please Confirm**:
* Respond with "**DEPLOYMENT SUCCESSFUL**" if your API is deployed and functioning correctly.
* Respond with "**DEPLOYMENT FAILED**" and provide error details if you encounter any issues.ttps://platform.openai.com/account/api-keys))
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
