# AI for Bharat Project (Neurolearn)

An AI-powered learning platform for beginner developers. Neurolearn explains code line-by-line, provides an interactive chat tutor, and tracks learning progress over time.

This repository currently contains product requirements and system design docs. Implementation is planned and will be added in subsequent milestones.

## Contents

- [What this is](#what-this-is)
- [Key capabilities](#key-capabilities)
- [Target stack](#target-stack)
- [Architecture overview](#architecture-overview)
- [Data model](#data-model)
- [Environment variables](#environment-variables)
- [Local development plan](#local-development-plan)
- [Testing strategy](#testing-strategy)
- [Repository map](#repository-map)
- [Roadmap](#roadmap)
- [Contributing](#contributing)

## What this is

Neurolearn is a hackathon-sized MVP focused on learning outcomes, not just answers. It provides code explanations, a context-aware chat assistant, and a personal history dashboard.

For full requirements and correctness properties, see:
- [requirements.md](requirements.md)
- [design.md](design.md)

## Key capabilities

- Code explanations for Python, JavaScript, Java, and C++
- Chat sessions with persistent context
- History dashboard for snippets and chats
- Rate limiting and usage tracking
- JWT-based authentication with refresh tokens

## Target stack

- Backend: Django REST Framework, JWT auth, OpenAI SDK
- Frontend: React + javascript , Vite, Monaco Editor, Tailwind
- Data: PostgreSQL (production), SQLite (development)

## Architecture overview

Three-layer architecture: React UI, Django REST API, and PostgreSQL/SQLite data layer. The AI engine is accessed via the API layer.

## Data model

Primary entities: `User`, `CodeSnippet`, `ChatSession`, `ChatMessage`, `APIUsage`. See [design.md](design.md) for schema details.

## Environment variables

The following variables are expected for the backend when implementation lands:

| Variable | Description |
| --- | --- |
| `DJANGO_SECRET_KEY` | Django secret key |
| `DATABASE_URL` | PostgreSQL connection string |
| `OPENAI_API_KEY` | AI provider API key |
| `JWT_ACCESS_TTL` | Access token lifetime (minutes) |
| `JWT_REFRESH_TTL` | Refresh token lifetime (days) |

## Local development plan

When the codebase is added, the expected workflow will be:

1. Clone the repository
2. Start the backend
3. Start the frontend

Backend (planned):
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r backend/requirements.txt
python backend/manage.py migrate
python backend/manage.py runserver
```

Frontend (planned):
```bash
cd frontend
npm install
npm run dev
```

## Testing strategy

Testing is designed around unit tests plus property-based tests. Planned tools:

- Backend: pytest, pytest-django, Hypothesis
- Frontend: Vitest, React Testing Library, fast-check

## Repository map

```
.
├── requirements.md     # Product requirements and acceptance criteria
├── design.md           # Architecture, API, and data model
└── README.md           # Project overview (this file)
```

## Roadmap

- MVP implementation for authentication, code explanation, and chat
- History dashboard and usage tracking
- Deployment guides and Docker assets

## Contributing

Contributions are welcome. If you want to help:

1. Open an issue describing the change
2. Fork and create a feature branch
3. Submit a pull request with a clear description and tests where applicable
