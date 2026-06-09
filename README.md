# Nexus — Auth Portal

FastAPI backend with JWT auth (cookie-based) + plain HTML/CSS/JS frontend.

## Stack

- **Backend** — FastAPI, SQLAlchemy, joserfc, passlib (argon2)
- **Frontend** — Vanilla HTML/CSS/JS (no build step)
- **DB** — SQLite (swap `DATABASE_URL` for Postgres in prod)

## Setup

```bash
git clone <repo-url>
cd <project>

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

pip install -r requirements.txt

cp .env.example .env             # fill in your values
```

## Run

```bash
cd app
uvicorn main:app --reload
```

Open `http://localhost:8000`

## API Routes

| Method | Route | Description |
|--------|-------|-------------|
| POST | `/register` | Create account |
| POST | `/login` | Login, sets cookie |
| GET | `/verify` | Get current user |
| POST | `/log-out` | Clear cookie |

## Project Structure

```
├── app/
│   ├── main.py       # routes
│   ├── auth.py       # JWT logic
│   ├── crud.py       # DB operations
│   ├── models.py     # SQLAlchemy models
│   ├── schema.py     # Pydantic schemas
│   ├── utils.py      # password hashing
│   ├── database.py   # DB session
│   └── config.py     # settings via .env
└── frontend/
    ├── index.html
    ├── app.js
    └── styles.css
```
