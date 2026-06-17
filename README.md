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

<table width="100%">
<tr>
<td width="33%" valign="top" align="left">

<strong>Intent-Aware Processing</strong><br><br>

Automatically classifies incoming requests into:

- Question
- Concept Exploration
- Delivery Requirement
- Ambiguous Request

Each request follows a different workflow path based on intent.

</td>
<td width="33%" valign="top" align="left">

<strong>AI-Guided Requirement Discovery</strong><br><br>

Uses a structured six-field requirement model:

- Business Objective
- Scope
- Data Sources
- Stakeholders
- Success Criteria
- Frequency

The platform dynamically determines whether to ask targeted questions, confirm inferred values, deepen understanding, or advance to review based on confidence scoring and completeness evaluation.

</td>
<td width="33%" valign="top" align="left">

<strong>Domain Intelligence Framework</strong><br><br>

MotionIQ includes domain-specific knowledge packages that provide:

- Business terminology
- Inference rules
- Clarification guidance
- Confirmation logic
- Enterprise context

This enables explainable business inference beyond generic LLM reasoning.

</td>
</tr>
<tr>
<td width="33%" valign="top" align="left">

<strong>Metadata-Aware Governance</strong><br><br>

MotionIQ evaluates requests against an enterprise asset catalog to identify:

- Reuse
- Extension
- New Build

opportunities before delivery artifacts are generated.

</td>
<td width="33%" valign="top" align="left">

<strong>Enterprise Retrieval and Grounding</strong><br><br>

Questions and concept exploration leverage a hybrid retrieval architecture:

- Semantic Retrieval
- BM25 Keyword Retrieval
- Re-ranking
- Sufficiency Validation
- Grounding Verification

This improves response quality while reducing hallucination risk.

</td>
<td width="33%" valign="top" align="left">

<strong>Automated Delivery Artifacts</strong><br><br>

Generates:

- Requirement Documents
- Epics
- User Stories
- Acceptance Criteria
- Jira Execution Packages

from a governed requirement state.

</td>
</tr>
<tr>
<td width="33%" valign="top" align="left">

<strong>Human-in-the-Loop Governance</strong><br><br>

Critical lifecycle transitions require explicit user approval.

Examples include:

- Approval
- Revision
- Jira Submission

The platform never promotes requirements autonomously.

</td>
<td width="33%" valign="top" align="left">

<strong>Versioned Requirement Lifecycle</strong><br><br>

Maintains immutable requirement snapshots across lifecycle transitions.

Supports:

- Requirement history
- Audit traceability
- Approval lineage
- Jira submission tracking

</td>
<td width="33%" valign="top" align="left">

<strong>Execution Package Generation</strong><br><br>

Creates Jira-ready execution outputs from approved requirement state, including epics, user stories, acceptance criteria, and delivery package structure.

</td>
</tr>
</table>

---



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

<table width="100%">
<tr>
<td width="33%" valign="top" align="left">

<strong>Platform Foundation</strong><br><br>

- Docker containerization
- Non-root container execution
- Environment-driven configuration
- Health monitoring endpoints
- Service dependency validation

</td>
<td width="33%" valign="top" align="left">

<strong>Persistence and State</strong><br><br>

- PostgreSQL persistence layer
- Redis-backed session management
- Immutable requirement versioning
- Jira submission logging

</td>
<td width="33%" valign="top" align="left">

<strong>Retrieval and Governance</strong><br><br>

- Hybrid semantic + BM25 retrieval
- Re-ranking pipeline
- Sufficiency validation
- Grounding verification
- Metadata-driven reuse recommendations

</td>
</tr>
<tr>
<td width="33%" valign="top" align="left">

<strong>Reliability Improvements</strong><br><br>

- Deterministic domain loading
- Enhanced LLM response validation
- Structured JSON parsing safeguards
- Model compatibility management
- Fail-fast Redis validation

</td>
<td width="33%" valign="top" align="left">

<strong>Runtime Health</strong><br><br>

- Application health endpoint
- Database status validation
- Redis status validation
- Index status validation
- Environment startup checks

</td>
<td width="33%" valign="top" align="left">

<strong>Container Readiness</strong><br><br>

- Docker Compose support
- Reproducible runtime setup
- Portable service configuration
- App, database, and Redis service separation
- Build validation support

</td>
</tr>
</table>

---

## Technology Stack

<table width="100%">
<tr>
<td width="33%" valign="top" align="left">

<strong>Frontend</strong><br><br>

- React
- JavaScript
- HTML5

</td>
<td width="33%" valign="top" align="left">

<strong>Backend</strong><br><br>

- FastAPI
- Python

</td>
<td width="33%" valign="top" align="left">

<strong>AI</strong><br><br>

- Anthropic Claude
- Sentence Transformers

</td>
</tr>
<tr>
<td width="33%" valign="top" align="left">

<strong>Retrieval</strong><br><br>

- Hybrid Search
- BM25
- Vector Similarity Search
- Semantic Search
- Re-ranking

</td>
<td width="33%" valign="top" align="left">

<strong>Data</strong><br><br>

- PostgreSQL
- Redis

</td>
<td width="33%" valign="top" align="left">

<strong>DevOps</strong><br><br>

- Docker
- SQLAlchemy
- Alembic

</td>
</tr>
<tr>
<td width="33%" valign="top" align="left">

<strong>Governance</strong><br><br>

- Deterministic routing
- Approval workflows
- Immutable version history
- Metadata-driven recommendations

</td>
<td width="33%" valign="top" align="left">

<strong>Integration</strong><br><br>

- Jira execution packages
- Metadata catalog checks
- Document ingestion
- Enterprise context enrichment

</td>
<td width="33%" valign="top" align="left">

<strong>Architecture Patterns</strong><br><br>

- Multi-agent architecture
- Deterministic orchestration
- Retrieval-Augmented Generation
- Human-in-the-loop governance
- State-driven lifecycle management

</td>
</tr>
</table>

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
