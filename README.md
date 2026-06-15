# MotionIQ

MotionIQ is an AI-powered Business Analyst and delivery-orchestration platform. It takes a business request expressed in natural language — a question, a vague idea, or a formal requirement — and walks it through a deterministic, governed pipeline:

1. Classifies the intent of the request (question, concept exploration, or delivery requirement).
2. Grounds questions and concept exploration in enterprise documents using hybrid retrieval (semantic + keyword search) with hallucination controls.
3. For delivery requirements, runs an iterative clarification dialogue until a requirement is "delivery ready," using a structured six-field requirement model.
4. Checks the requirement against an enterprise metadata/asset catalog to recommend **reuse**, **extension**, or **new build**.
5. Generates a requirement document, an epic, and user stories, with full version history.
6. Produces a Jira-ready execution package and, on approval, submits it directly to Jira.

For the full architecture and business case — including the multi-agent design, retrieval pipeline, governance model, and production roadmap.

## Architecture at a Glance

- **Backend**: FastAPI (`src/api`), orchestrating a 9-node deterministic graph (`src/graph/orchestration_graph.py`) that routes each request through intent classification, retrieval/grounding, metadata checks, and the BA (requirement) workflow.
- **Frontend**: Single-file React SPA (`frontend/index.html`) with component files in `frontend/components/` (`chat.jsx`, `sidebar.jsx`, `review.jsx`, `api.jsx`). No build toolchain.
- **Retrieval**: Hybrid semantic (SentenceTransformer) + BM25 keyword search, merged and re-ranked, with grounding verification to reduce hallucination risk.
- **Persistence**: PostgreSQL (requirements, immutable version history, Jira submission logs) via SQLAlchemy + Alembic; Redis-backed session store with in-memory fallback.

## Configuration

All configuration is environment-driven via `.env` (see `.env.example` for the full list):

| Variable | Purpose |
|---|---|
| `ANTHROPIC_API_KEY` | Required for all LLM-backed reasoning (classification, clarification, artifact generation, summarization). |
| `DATABASE_URL` | PostgreSQL connection string — required for the requirement lifecycle and Alembic migrations. |
| `REDIS_URL` / `REDIS_REQUIRED` | Session store backend. Leave `REDIS_URL` empty for an in-memory fallback (local dev only). |
| `SESSION_TTL_SECONDS` | Session expiry (default 24h). |
| `JIRA_*` | Optional — leave blank to disable Jira submission; all other features work without it. |
| `APP_USER_*` | Display identity shown in the UI. |

## Project Status

MotionIQ is a proof-of-concept. Phase 1 production-readiness work (containerization, health monitoring, CI build validation, non-root execution) is complete.
