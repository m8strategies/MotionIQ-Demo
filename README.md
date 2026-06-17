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

<table>
<tr>
<td width="33%">

### Intent-Aware Processing

Automatically classifies requests into:

- Question
- Concept Exploration
- Delivery Requirement
- Ambiguous Request

Each request follows a specialized workflow path.

</td>

<td width="33%">

### AI-Guided Requirement Discovery

Uses a structured six-field requirement model:

- Business Objective
- Scope
- Data Sources
- Stakeholders
- Success Criteria
- Frequency

Drives iterative clarification using confidence scoring.

</td>

<td width="33%">

### Domain Intelligence Framework

Provides:

- Business terminology
- Inference rules
- Clarification guidance
- Confirmation logic
- Enterprise context

Enables explainable business inference beyond generic LLM reasoning.

</td>
</tr>

<tr>
<td>

### Metadata-Aware Governance

Evaluates requests against enterprise assets to identify:

- Reuse
- Extension
- New Build

opportunities before delivery begins.

</td>

<td>

### Enterprise Retrieval & Grounding

Hybrid retrieval architecture:

- Semantic Search
- BM25 Search
- Re-ranking
- Sufficiency Validation
- Grounding Verification

Designed to reduce hallucination risk.

</td>

<td>

### Automated Delivery Artifacts

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
<td>

### Human-in-the-Loop Governance

Critical lifecycle transitions require explicit approval:

- Approve
- Revise
- Submit to Jira

The platform never promotes requirements autonomously.

</td>

<td>

### Immutable Version History

Captures requirement snapshots at every lifecycle transition.

Supports:

- Auditability
- Traceability
- Point-in-Time Reconstruction

</td>

<td>

### Jira Delivery Integration

Creates execution-ready Jira payloads and supports governed Jira submission workflows.

</td>
</tr>
</table>

---

## Architecture at a Glance

<table>
<tr>
<td width="33%">

### Frontend

React Single Page Application

Features:

- Conversational Intake Interface
- Review Workspace
- Requirement Dashboard
- Session Navigation

</td>

<td width="33%">

### Backend

FastAPI-based orchestration platform responsible for:

- Request Processing
- Workflow Orchestration
- State Management
- Retrieval Services
- Artifact Generation
- Jira Integration

</td>

<td width="33%">

### Orchestration Engine

Deterministic 9-node orchestration graph responsible for:

1. Intent Classification
2. Ambiguity Resolution
3. Requirement Shape Resolution
4. Metadata Evaluation
5. Context Enrichment
6. Clarification Workflow
7. Confidence Evaluation
8. Artifact Generation
9. Lifecycle Management

</td>
</tr>

<tr>
<td>

### Multi-Agent Design

Specialized bounded agents:

- LeaderAgent
- MeaningAgent
- MetadataAgent
- ContextAgent

Each operates within deterministic workflow boundaries.

</td>

<td>

### Domain Intelligence Layer

Business context engine providing:

- Domain Knowledge
- Inference Rules
- Clarification Guidance
- Confirmation Logic
- Enterprise Terminology

Influences requirement shaping and discovery.

</td>

<td>

### Retrieval Architecture

Hybrid retrieval pipeline:

1. Semantic Search
2. BM25 Keyword Search
3. Score Normalization
4. Re-ranking
5. Sufficiency Gate
6. Grounding Verification

Built for enterprise knowledge retrieval.

</td>
</tr>

<tr>
<td>

### State Management

Three-tier architecture:

- Per-Turn State
- Session State (Redis)
- Requirement State (PostgreSQL)

Supports orchestration, continuity, and auditability.

</td>

<td>

### Governance Framework

Three governance layers:

- Routing Governance
- Lifecycle Governance
- Audit Governance

Provides explainability and control.

</td>

<td>

### Persistence Layer

PostgreSQL stores:

- Requirements
- Version History
- Jira Submission Logs

Redis manages conversational continuity and workflow state.

</td>
</tr>
</table>

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

- Requirement Versions
- Lifecycle History
- Approval Records
- Jira Submission History

---

## Production Readiness

<table>
<tr>
<td width="33%">

### Containerization

- Docker Deployment
- Environment Isolation
- Reproducible Builds
- Portable Runtime Environment

</td>

<td width="33%">

### Health Monitoring

- Health Endpoints
- Startup Validation
- Dependency Checks
- Service Availability Monitoring

</td>

<td width="33%">

### Security Foundation

- Non-Root Container Execution
- Environment-Based Secrets
- Controlled Service Access
- Session Isolation

</td>
</tr>

<tr>
<td>

### Persistence & Recovery

- PostgreSQL Persistence
- Requirement Versioning
- Jira Submission History
- Durable State Management

</td>

<td>

### Reliability Engineering

- Redis Fail-Fast Validation
- Deterministic Workflow Execution
- Structured Error Handling
- Configuration Validation

</td>

<td>

### Retrieval Reliability

- Hybrid Search Architecture
- Grounding Validation
- Sufficiency Controls
- Re-ranking Pipeline

</td>
</tr>

<tr>
<td>

### Governance Controls

- Lifecycle Approvals
- Audit Snapshots
- Human-in-the-Loop Validation
- Metadata-Based Recommendations

</td>

<td>

### Operational Stability

- Structured Logging
- Environment Standardization
- Service Health Validation
- Deterministic Domain Resolution

</td>

<td>

### Recent Enhancements

- Domain Rule Evaluation Controls
- Improved LLM Response Validation
- JSON Parsing Hardening
- Model Compatibility Management

</td>
</tr>
</table>

---

## Technology Stack

<table>
<tr>
<td width="33%">

### Frontend

- React
- JavaScript
- HTML5
- CSS

</td>

<td width="33%">

### Backend

- Python
- FastAPI
- SQLAlchemy
- Alembic

</td>

<td width="33%">

### AI & Reasoning

- Anthropic Claude
- Prompt Engineering
- Domain Inference
- Confidence Scoring

</td>
</tr>

<tr>
<td>

### Retrieval

- Sentence Transformers
- BM25
- Hybrid Search
- Re-ranking

</td>

<td>

### Data & Persistence

- PostgreSQL
- Redis
- Versioned Requirements
- Session Management

</td>

<td>

### DevOps

- Docker
- Docker Compose
- Environment Configuration
- Container Health Monitoring

</td>
</tr>

<tr>
<td>

### Governance

- Rule Engine
- Lifecycle Controls
- Approval Workflows
- Audit History

</td>

<td>

### Integration

- Jira API
- Enterprise Metadata Catalog
- Document Ingestion
- Asset Reuse Evaluation

</td>

<td>

### Architecture Patterns

- Multi-Agent Architecture
- Deterministic Orchestration
- RAG
- Human-in-the-Loop AI

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

- End-to-End Requirement Lifecycle
- Deterministic Orchestration Engine
- Multi-Agent Architecture
- Hybrid Retrieval Pipeline
- Domain Intelligence Framework
- Metadata-Aware Governance
- Artifact Generation
- Jira Integration
- PostgreSQL Persistence
- Redis Session Management
- Containerized Deployment

### In Progress

- Production Hardening
- Observability & Telemetry
- Multi-Model Orchestration
- Configuration-Driven Workflow Extensibility
- Enterprise Deployment Readiness

---

## Project Vision

MotionIQ demonstrates how AI can move beyond conversational assistance into governed delivery execution.

The platform combines enterprise retrieval, deterministic orchestration, domain intelligence, lifecycle governance, and human oversight to transform natural-language business requests into structured, reviewable, and execution-ready delivery artifacts.
