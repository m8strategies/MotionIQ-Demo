# MotionIQ

MotionIQ is an AI-powered Business Analyst and delivery-orchestration platform. It takes a business request expressed in natural language — a question, a vague idea, or a formal requirement — and walks it through a deterministic, governed pipeline:

1. Classifies the intent of the request (question, concept exploration, or delivery requirement).
2. Grounds questions and concept exploration in enterprise documents using hybrid retrieval (semantic + keyword search) with hallucination controls.
3. For delivery requirements, runs an iterative clarification dialogue until a requirement is "delivery ready," using a structured six-field requirement model.
4. Checks the requirement against an enterprise metadata/asset catalog to recommend **reuse**, **extension**, or **new build**.
5. Generates a requirement document, an epic, and user stories, with full version history.
6. Produces a Jira-ready execution package and, on approval, submits it directly to Jira.

## How It Works

**Example:** A product manager types: *"Finance needs a dashboard for regional profitability."*

1. **Classification** — Leader agent classifies the input as a delivery requirement with subtype `interactive_dashboard`.
2. **Asset catalog check** — Metadata agent searches the enterprise catalog and flags two existing regional KPI datasets as reuse candidates, recommending extension over new build.
3. **Clarification dialogue** — The system asks targeted questions to fill the six-field requirement model (Business Objective, Scope, Stakeholders, Data Sources, Frequency, Success Criteria). The PM answers over 2–3 turns until the confidence gate passes.
4. **Artifact generation** — BA agent generates a structured requirement document, an epic ("Regional Profitability Intelligence"), and user stories with acceptance criteria. A version snapshot is written to the database.
5. **Human approval** — The review tab presents the full package. The PM clicks **Submit to Jira**.
6. **Jira submission** — The system builds the Jira payload and posts it. A submission log entry is written with the response, timestamp, and requirement version.

Total time from first message to Jira ticket: typically under 10 minutes.

## Quick Start (Docker)

```bash
# Copy and fill in environment variables
cp .env.example .env

# Start the full stack (app, redis, db migrations)
docker compose up -d

# First run only: named volumes for index/uploads/data start empty,
# so populate the retrieval index from the documents already under data/
docker compose exec app python -m src.bootstrap_index

# Check health
curl http://localhost:8000/health
```

The app is served at `http://localhost:8000/app`.

## Local Development (without Docker)

```bash
# Install dependencies
pip install -r requirements.txt

# Run the API server
uvicorn src.api.main:app --reload

# Run all tests
pytest tests/

# Run a single test file
pytest tests/test_phase1.py -v

# Build the document retrieval index (after uploading documents via /ingest)
python src/build_index.py
```

The server runs at `http://127.0.0.1:8000`. The React SPA is served at `/app` directly from FastAPI — no separate frontend build step (React and Babel load via CDN in `frontend/index.html`).

## Architecture at a Glance

- **Backend**: FastAPI (`src/api`), orchestrating a 9-node deterministic graph (`src/graph/orchestration_graph.py`) that routes each request through intent classification, retrieval/grounding, metadata checks, and the BA (requirement) workflow.
- **Frontend**: Single-file React SPA (`frontend/index.html`) with component files in `frontend/components/` (`chat.jsx`, `sidebar.jsx`, `review.jsx`, `api.jsx`). No build toolchain.
- **Retrieval**: Hybrid semantic (SentenceTransformer) + BM25 keyword search, merged and re-ranked, with grounding verification to reduce hallucination risk.
- **Persistence**: PostgreSQL (requirements, immutable version history, Jira submission logs) via SQLAlchemy + Alembic; Redis-backed session store with in-memory fallback.
- **Multi-agent orchestration**: Nine specialised agents (Leader, Meaning, Metadata, Context, Decision Engine, Questioning, BA, Artifact Generation, Retrieval) collaborate under a deterministic 9-node graph. AI reasoning is bounded within each agent's role; control flow between agents is explicit and inspectable via a single `route` state field — not LLM-driven.
- **Governance**: Six-field requirement model (Business Objective, Scope, Stakeholders, Data Sources, Frequency, Success Criteria) with confidence-based readiness gates. Every requirement has an immutable version history snapshot at each lifecycle transition. No requirement reaches Jira without explicit human approval — generate-then-review-then-submit, never automatic.
- **Model routing**: Three-tier abstraction (`src/services/llm_client.py`) — FAST, STANDARD, HEAVY — all defaulting to `claude-sonnet-4-6` unless overridden by environment variable. Reflection generation routes to FAST (`claude-haiku-4-5-20251001`); all other services use STANDARD.

## Configuration

All configuration is environment-driven via `.env` (see `.env.example` for the full list):

| Variable | Purpose |
|---|---|
| `ANTHROPIC_API_KEY` | Required for all LLM-backed reasoning (classification, clarification, artifact generation, summarization). |
| `DATABASE_URL` | PostgreSQL connection string — required for the requirement lifecycle and Alembic migrations. |
| `REDIS_URL` / `REDIS_REQUIRED` | Session store backend. Leave `REDIS_URL` empty for an in-memory fallback (local dev only). |
| `SESSION_TTL_SECONDS` | Session expiry (default 24h). |
| `FAST_MODEL` | Override the FAST tier model (default: `claude-sonnet-4-6`). Set to `claude-haiku-4-5-20251001` to activate cost-optimised routing for reflection generation. |
| `STANDARD_MODEL` | Override the STANDARD tier model (default: `claude-sonnet-4-6`). |
| `HEAVY_MODEL` | Override the HEAVY tier model (default: `claude-sonnet-4-6`). Reserved for future high-complexity routing (e.g. artifact generation). |
| `JIRA_*` | Optional — leave blank to disable Jira submission; all other features work without it. |
| `APP_USER_*` | Display identity shown in the UI. |

## Project Status

MotionIQ is a proof-of-concept rated **Production-Adjacent** as of 2026-06-16.

Completed work:
- **Phase 1**: Containerization, health monitoring, CI build validation, non-root execution, Alembic migrations as a pre-start service.
- **Stabilization**: Fixed slot extractor `when_any` evaluation, reflection JSON parsing, domain loader sort determinism, and a silent deprecated-model defect in `artifact_service` and `classification_fallback_service`.
- **Multi-model routing**: Three-tier model abstraction live; reflection generation validated and promoted to FAST tier (~8x cost reduction); classification fallback evaluated and kept on STANDARD.

Known gaps — no API authentication, no LLM retry logic, silent exception swallowing in several services, 34 failing tests, mock metadata catalog, deferred context-summary reuse.
