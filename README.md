# Vue + FastAPI Full-Stack Template

A modern full-stack template featuring a Reactivity-driven Frontend with Vue 3 (Composition API + TypeScript) and a typed Backend powered by FastAPI (Python 3).

## Project Structure

```text
.
├── backend/            # FastAPI backend
│   ├── main.py         # Entry point for backend API
│   └── requirements.txt# Backend dependencies
├── frontend/           # Vue 3 + TypeScript frontend (Vite)
│   ├── src/            # Frontend source code
│   └── vite.config.ts  # Vite configuration (includes API proxy)
└── README.md           # This file
```

## Quick Start

### 1. Start the Backend (FastAPI)

Requires Python 3.8+ installed.

```bash
# From the root directory
# 1. Create a virtual environment
python -m venv venv

# 2. Activate the virtual environment
# On Windows:
.\venv\Scripts\activate
# On Linux/macOS:
# source venv/bin/activate

# 3. Install dependencies
pip install -r backend/requirements.txt

# 4. Run the development server
cd backend
uvicorn main:app --reload
```

The backend API will be available at [http://127.0.0.1:8000](http://127.0.0.1:8000). You can visit [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs) for the interactive Swagger UI.

### 2. Start the Frontend (Vue)

Requires Node.js (v18+) installed.

```bash
# Open a new terminal and navigate to the frontend directory
cd frontend

# 1. Install dependencies
npm install

# 2. Run the development server
npm run dev
```

The Vue app will be available at [http://localhost:5173](http://localhost:5173).

## Features Included

- **FastAPI** with CORS middleware configured out of the box.
- **Vue 3** utilizing `script setup` composition API style, built with Vite.
- Proxy setup in `vite.config.ts` to seamlessly route `/api` requests to the backend, avoiding CORS issues entirely in development.
- Initial fetch logic in `App.vue` that communicates with the `Hello World` endpoint of the backend.
