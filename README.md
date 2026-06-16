# MotionIQ

MotionIQ is an AI-powered Business Analyst and delivery orchestration platform that transforms natural-language business requests into governed, execution-ready delivery artifacts.

The platform combines deterministic workflow orchestration, enterprise retrieval, domain intelligence, metadata-driven governance, human-in-the-loop controls, and automated artifact generation to accelerate the path from business idea to implementation.

**Core Principle**

> AI provides recommendations. The system governs decisions.

---

## What MotionIQ Does

MotionIQ takes a business request expressed in natural language and guides it through a structured requirement lifecycle.

1. Classifies the request as a question, concept exploration, delivery requirement, or ambiguous request.
2. Grounds questions and concept exploration in enterprise knowledge using hybrid retrieval and hallucination controls.
3. Uses domain-aware inference and a structured six-field requirement model to drive iterative requirement discovery.
4. Evaluates requests against an enterprise asset catalog to identify reuse, extension, or new-build opportunities.
5. Applies confidence scoring and deterministic decision logic to determine the next best action.
6. Generates review-ready delivery artifacts including requirement documents, epics, user stories, and acceptance criteria.
7. Maintains immutable version history throughout the lifecycle.
8. Produces Jira-ready execution packages and supports governed Jira submission.

---

## Key Capabilities

### Intent-Aware Processing

Automatically classifies incoming requests into:

- Question
- Concept Exploration
- Delivery Requirement
- Ambiguous Request

Each request follows a different workflow path based on intent.

### AI-Guided Requirement Discovery

Uses a structured six-field requirement model:

- Business Objective
- Scope
- Data Sources
- Stakeholders
- Success Criteria
- Frequency

The platform dynamically determines whether to:

- Ask targeted questions
- Confirm inferred values
- Deepen understanding
- Advance to review

based on confidence scoring and completeness evaluation.

### Domain Intelligence Framework

MotionIQ includes domain-specific knowledge packages that provide:

- Business terminology
- Inference rules
- Clarification guidance
- Confirmation logic
- Enterprise context

This enables explainable business inference beyond generic LLM reasoning.

### Metadata-Aware Governance

MotionIQ evaluates requests against an enterprise asset catalog to identify:

- Reuse
- Extension
- New Build

opportunities before delivery artifacts are generated.

### Enterprise Retrieval & Grounding

Questions and concept exploration leverage a hybrid retrieval architecture:

- Semantic Retrieval
- BM25 Keyword Retrieval
- Re-ranking
- Sufficiency Validation
- Grounding Verification

This improves response quality while reducing hallucination risk.

### Automated Delivery Artifacts

Generates:

- Requirement Documents
- Epics
- User Stories
- Acceptance Criteria
- Jira Execution Packages

from a governed requirement state.

### Human-in-the-Loop Governance

Critical lifecycle transitions require explicit user approval.

Examples include:

- Approval
- Revision
- Jira Submission

The platform never promotes requirements autonomously.

---

## Architecture at a Glance

### Frontend

- React Single Page Application
- Conversational Intake Interface
- Review Workspace
- Requirement Dashboard
- Session Management

### Backend

FastAPI-based orchestration platform responsible for:

- Request processing
- Workflow orchestration
- State management
- Retrieval services
- Artifact generation
- Jira integration

### Orchestration Engine

MotionIQ executes requests through a deterministic 9-node orchestration graph responsible for:

1. Intent Classification
2. Ambiguity Resolution
3. Requirement Shape Resolution
4. Metadata Evaluation
5. Context Enrichment
6. Clarification Workflow
7. Confidence Evaluation
8. Artifact Generation
9. Lifecycle Management

### Multi-Agent Design

MotionIQ uses specialized bounded agents:

| Agent | Responsibility |
|---------|---------|
| LeaderAgent | Workflow orchestration and coordination |
| MeaningAgent | Requirement shape identification |
| MetadataAgent | Asset catalog analysis and reuse recommendations |
| ContextAgent | Retrieval, grounding, and contextual enrichment |

Each agent operates within deterministic workflow boundaries.

### Domain Intelligence Layer

The domain intelligence framework acts as a business context engine that enhances requirement discovery and inference.

Domain packages contain:

- Business terminology
- Inference rules
- Clarification guidance
- Confirmation logic
- Enterprise context
- Domain-specific assumptions

Examples include:

- Customer
- Finance
- Analytics
- Reporting
- Governance
- Data Engineering

The domain layer influences:

- Requirement shaping
- Slot extraction
- Inference generation
- Clarification prioritization
- Decision engine recommendations

### Retrieval Architecture

Hybrid retrieval pipeline:

1. Semantic Search
2. BM25 Keyword Search
3. Score Normalization
4. Re-ranking
5. Sufficiency Gate
6. Grounding Verification

Default configuration:

```text
Semantic Weight: 0.60
Keyword Weight: 0.40

Hybrid Weight: 0.70
Coverage Weight: 0.30
```

### State Management

MotionIQ uses a three-tier state architecture.

#### Per-Turn State

Ephemeral orchestration state used during graph execution.

#### Session State

Redis-backed conversational continuity and workflow context.

#### Requirement State

PostgreSQL system of record containing:

- Requirements
- Version History
- Jira Submission Logs

---

## Governance Framework

MotionIQ implements three independent governance layers.

### Routing Governance

AI components operate within explicitly bounded responsibilities. Workflow routing is controlled by deterministic orchestration logic.

### Lifecycle Governance

Critical lifecycle transitions require explicit user actions and approval.

Examples include:

- APPROVE
- REVISE
- SEND_TO_JIRA

### Audit Governance

Every lifecycle transition generates immutable version snapshots that provide a complete, reconstructable audit trail.

MotionIQ maintains:

- Requirement versions
- Lifecycle history
- Approval records
- Jira submission history

---

## Production Readiness

Completed engineering improvements include:

### Platform Foundation

- Docker containerization
- Non-root container execution
- Environment-driven configuration
- Health monitoring endpoints
- Service dependency validation

### Persistence & State

- PostgreSQL persistence layer
- Redis-backed session management
- Immutable requirement versioning
- Jira submission logging

### Retrieval & Governance

- Hybrid semantic + BM25 retrieval
- Re-ranking pipeline
- Sufficiency validation
- Grounding verification
- Metadata-driven reuse recommendations

### Reliability Improvements

- Deterministic domain loading
- Enhanced LLM response validation
- Structured JSON parsing safeguards
- Model compatibility management
- Fail-fast Redis validation

---

## Technology Stack

### Frontend

- React
- JavaScript
- HTML5

### Backend

- FastAPI
- Python

### AI

- Anthropic Claude
- Sentence Transformers

### Retrieval

- Hybrid Search
- BM25
- Vector Similarity Search

### Data

- PostgreSQL
- Redis

### DevOps

- Docker
- SQLAlchemy
- Alembic

---

## Configuration

All configuration is environment-driven via `.env` (see `.env.example`).

| Variable | Purpose |
|---|---|
| `ANTHROPIC_API_KEY` | Required for LLM-backed reasoning and artifact generation |
| `DATABASE_URL` | PostgreSQL connection string |
| `REDIS_URL` | Session persistence backend |
| `REDIS_REQUIRED` | Enforce Redis availability |
| `SESSION_TTL_SECONDS` | Session expiration configuration |
| `JIRA_*` | Optional Jira integration settings |
| `APP_USER_*` | Display identity shown in UI |

---

## Current Status

### Completed

- End-to-end requirement lifecycle
- Deterministic orchestration engine
- Multi-agent architecture
- Hybrid retrieval pipeline
- Domain intelligence framework
- Metadata-aware governance
- Artifact generation
- Jira integration
- PostgreSQL persistence
- Redis session management
- Containerized deployment

### In Progress

- Production hardening
- Observability and telemetry
- Multi-model orchestration
- Configuration-driven workflow extensibility
- Enterprise deployment readiness

---

## Project Vision

MotionIQ demonstrates how AI can move beyond conversational assistance into governed delivery execution.

The platform combines enterprise retrieval, deterministic orchestration, domain intelligence, lifecycle governance, and human oversight to transform natural-language business requests into structured, reviewable, and execution-ready delivery artifacts.
