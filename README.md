# GovContinue - Government Institutional Knowledge Continuity System

[![Project Status: Specification & Architecture](https://img.shields.io/badge/Status-Specification%20%26%20Architecture-blue.svg)](#12-current-project-status)
[![Domain](https://img.shields.io/badge/Domain-GovTech%20%2F%20Knowledge%20Management-green.svg)](#1-project-overview)
[![Academic](https://img.shields.io/badge/SIH%202026-MCA%20SAPM%20Design-orange.svg)](#14-contributors)
[![Python](https://img.shields.io/badge/Python-3.11%2B-blue?logo=python)](#8-prerequisites)
[![Node.js](https://img.shields.io/badge/Node.js-v20%2B%20%2F%20v24%2B-green?logo=node.js)](#8-prerequisites)
[![License: Not Specified](https://img.shields.io/badge/License-Not%20Specified-lightgrey.svg)](#15-license)

> **A secure, evidence-backed institutional knowledge-continuity and AI handover layer for government departments.**

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Problem Statement](#2-problem-statement)
3. [Project Objectives](#3-project-objectives)
4. [Key Features & Capabilities](#4-key-features--capabilities)
5. [System Architecture & Workflow](#5-system-architecture--workflow)
6. [Technology Stack](#6-technology-stack)
7. [Repository Structure](#7-repository-structure)
8. [Prerequisites](#8-prerequisites)
9. [Installation & Local Setup](#9-installation--local-setup)
10. [How to Run (Development)](#10-how-to-run-development)
11. [Security, RBAC & Governance](#11-security-rbac--governance)
12. [Current Project Status](#12-current-project-status)
13. [Future Scope & Roadmap](#13-future-scope--roadmap)
14. [Contributors](#14-contributors)
15. [License](#15-license)

---

## 1. Project Overview

Government departments routinely generate and store massive volumes of information across departmental files, inspection reports, meeting minutes, administrative orders, grievance logs, spreadsheets, and digital office systems (such as e-Office). When officers or staff members are transferred, promoted, or retired, these records remain preserved within the department.

However, a fundamental operational breakdown occurs during personnel transitions: **the operational context connecting those records is lost or fractured**. An incoming officer inheriting a desk must spend weeks or months sifting through disconnected files to answer essential operational questions:

- **What decisions were made and why?**
- **What solutions were already attempted, and did they succeed or fail?**
- **What critical tasks, contractor corrections, or site inspections remain pending?**
- **What citizen grievances require immediate administrative intervention?**

**GovContinue** addresses this challenge by functioning as an **institutional intelligence and continuity layer** situated above existing government record systems. It does not replace document management systems, HR databases, or official administrative workflows. Instead, it processes authorized project records, extracts relationships between events and decisions, tracks unresolved dependencies and risks, and prepares an **evidence-backed transition brief** to enable seamless officer onboarding.

---

## 2. Problem Statement

### Context Reconstruction vs. Document Availability

The core issue in government employee handovers is commonly mischaracterized as missing records. In practice, official records are preserved in departmental archives or digital repositories. The true challenge is **context reconstruction**:

1. **Scattered Operational Memory**: Information regarding a single public initiative (such as a municipal drainage project or highway contract) is fragmented across inspection reports, vendor correspondence, financial sanctions, and grievance databases.
2. **High Handover Latency**: Successors require significant time to understand multi-year project histories, delaying urgent interventions and public service delivery.
3. **Repeated Mistakes & Reversals**: Without access to historical rationales and prior failed approaches, incoming personnel risk repeating past procedural errors or inadvertently reversing deliberate policy determinations.
4. **Lack of Traceable Evidence**: Conventional keyword search engines return lists of isolated documents, forcing officers to manually verify whether a past decision was officially sanctioned or superseded.

```text
Existing Transition Dilemma:
Departmental Records Exist  ──▶  Officer Transferred  ──▶  Successor Inherits Raw Files
                                                                  │
                                            ┌─────────────────────┴─────────────────────┐
                                            ▼                                           ▼
                                 Weeks Spent Re-reading                      Unresolved Issues & Risks
                                 Disconnected Documents                      Overlooked During Transition
```

---

## 3. Project Objectives

- **Preserve Institutional Knowledge**: Safeguard administrative memory beyond individual officer tenures by structuring context across events, decisions, and outcomes.
- **Synthesize Multi-Source Government Records**: Transform siloed reports, inspection notes, meeting minutes, and official orders into a coherent project timeline and relationship model.
- **Provide Instant Transition Intelligence**: Supply incoming officers with an automated, role-authorized **Transition Brief** outlining top priorities, pending tasks, recent decisions, and active risks.
- **Deliver Evidence-Backed AI Assistance**: Ensure all AI-generated summaries, answers, and risk assessments are strictly anchored to verified source documents with citations (document title, date, and paragraph/page).
- **Enforce Strict Role-Based Access Control**: Ensure that access to sensitive departmental records adheres strictly to the principle of least privilege, preventing unauthorized data retrieval.

---

## 4. Key Features & Capabilities

The features below are defined based on the project design specifications and architectural blueprints. Implementation status is clearly indicated for each module:

| Feature Area | Description | Implementation Status |
| :--- | :--- | :--- |
| **Document Ingestion & Processing** | Ingestion pipeline for authorized records (PDFs, inspection reports, orders, minutes), text extraction, and metadata tagging. | `Planned` |
| **Knowledge Extraction Engine** | Extraction of core administrative entities: project codes, dates, responsible officers, contractors, decisions, and problem statements. | `Planned` |
| **Institutional Knowledge Graph** | Cross-record relational modeling linking projects, officers, contractors, inspections, decisions, and citizen complaints. | `Planned` |
| **Chronological Timeline Engine** | Reconstruction of multi-year project milestones, design revisions, sanctions, and site visits in chronological sequence. | `Planned` |
| **Decision Intelligence & Tracking** | Structured capture of key decisions, rationales, supporting evidence, and subsequent operational impacts. | `Planned` |
| **Pending Work & Risk Detection** | Automated flagging of delayed milestones (>90 days), recurring inspection defects, and unresolved public grievances. | `Planned` |
| **Role-Authorized Handover Brief** | Automated briefing dashboard for incoming personnel highlighting critical focus areas upon assuming office. | `Planned` |
| **AI / RAG Question Answering** | Context-restricted retrieval-augmented generation allowing officers to query project history with verbatim citations. | `Planned` |
| **Strict Evidence Attribution** | Verification mechanism ensuring every AI statement references document source, date, and section (preventing hallucination). | `Planned` |
| **Role-Based Access Control (RBAC)** | Access enforcement at the project and department level prior to vector search and model retrieval. | `Planned` |
| **Comprehensive Audit Logging** | Immutable logging of authentication, document views, AI queries, and data access for compliance. | `Planned` |

> [!NOTE]
> **Implementation Note**: The repository currently holds the foundational project specifications, software architectural designs (MCA SAPM Design Levels), and system blueprints. Application source code modules are in the pre-implementation / specification phase.

---

## 5. System Architecture & Workflow

### Architectural Flowchart

```mermaid
flowchart TD
    A[Authorized Government Records\nReports, Orders, Minutes, Grievances] --> B[Data Processing & Classification\nText Extraction & Metadata Tagging]
    B --> C[Knowledge Extraction\nEntity & Relationship Detection]
    C --> D[Institutional Knowledge Model\nTimeline, Decisions, Risks, Pending Items]
    D --> E{User Authentication & RBAC Filter}
    E -->|Authorized Query| F[AI / RAG Retrieval Layer\nPermitted Context Only]
    E -->|Unauthorized| G[Access Denied & Audit Logged]
    F --> H[Evidence Verification Engine\nAttaches Document & Date Citations]
    H --> I[Officer Handover Dashboard\nTransition Brief, Timeline, Q&A]
```

### Pipeline Stages

1. **Authorized Ingestion**: Consumes authorized digital records from departmental document repositories.
2. **Text & Metadata Extraction**: Cleans input files and tags metadata (date, issuing officer, department, classification).
3. **Knowledge Modeling**: Links related entities into a connected graph (e.g., `Officer A` managed `Project P102` -> `Inspection I32` found defect -> `Decision D45` paused contractor payment).
4. **Pre-Retrieval Authorization**: User authentication and role/project clearance are verified **before** database search or vector retrieval occurs.
5. **Contextual AI / RAG**: Generates summaries and answers restricted solely to authorized context passages.
6. **Officer Handover Interface**: Presents the incoming employee with an executive brief, priority pending tasks, historical timeline, and evidence-backed Q&A.

---

## 6. Technology Stack

The system architecture is organized as a layered modular monolith to balance rapid academic prototyping with enterprise-grade modularity:

| Tier | Component | Technology / Tool | Role in GovContinue |
| :--- | :--- | :--- | :--- |
| **Frontend** | User Interface | **React / Next.js** | Interactive officer dashboards, handover brief, timeline view, and Q&A chat. |
| **Backend** | Application API | **FastAPI (Python 3.11+)** | High-performance asynchronous REST API, business logic, and security rules. |
| **Database** | Relational Store | **PostgreSQL** | Primary store for users, roles, projects, decisions, pending items, and audit logs. |
| **Search / Vector** | Similarity Index | **pgvector / OpenSearch** | Vector embeddings store for semantic document search across permitted records. |
| **Storage** | Document Store | **Object Storage (S3 / MinIO)** | Secure immutable storage for source PDFs, inspection orders, and attachments. |
| **AI / NLP** | RAG Pipeline | **Python NLP, LangChain / LlamaIndex** | Information extraction, contextual retrieval, and citation verification. |
| **DevOps** | Containerization | **Docker & GitHub Actions** | Standardized container builds and automated code quality checks. |

---

## 7. Repository Structure

```text
GovContinue/
├── README.md                           # Master project documentation
├── docs/                               # System design and architecture specifications
│   ├── architectural_design.md         # Multi-tier architectural specifications
│   ├── data_design.md                  # Entity relationships and data dictionary
│   └── security_model.md               # RBAC and data protection guidelines
├── frontend/                           # (Planned) React / Next.js web application
│   ├── public/                         # Static assets and UI icons
│   └── src/                            # Component hierarchy, dashboards, and API clients
├── backend/                            # (Planned) FastAPI application services
│   ├── app/
│   │   ├── api/                        # Route handlers (auth, projects, handover, rag)
│   │   ├── core/                       # Configuration, security tokens, role policies
│   │   ├── models/                     # Database schema models (SQLAlchemy / SQLModel)
│   │   ├── services/                   # Knowledge extraction, timeline, and RAG pipelines
│   │   └── utils/                      # Document text extractors and parsers
│   ├── requirements.txt                # Python package dependencies
│   └── Dockerfile                      # Backend container definition
└── data/                               # (Planned) Prototype synthetic data
    ├── raw_documents/                  # Synthetic departmental reports and orders
    └── synthetic_dataset.json          # Mock projects, employees, and inspection logs
```

---

## 8. Prerequisites

The following software environments are verified on the development system:

- **Operating System**: Windows / Linux / macOS
- **Python**: `3.11.x` or higher *(verified: Python 3.11.9)*
- **Node.js**: `v20.x` or `v24.x` *(verified: Node v24.13.0)*
- **Package Managers**: `pip` (Python), `npm` *(verified: 11.6.2)*
- **Version Control**: `git` *(verified: 2.53.0)*
- **Database (Target)**: PostgreSQL 15+ *(with pgvector extension)*

---

## 9. Installation & Local Setup

### 1. Clone the Repository
```bash
git clone https://github.com/devanshu-k09/GovContinue.git
cd GovContinue
```

### 2. Backend Environment Setup (Planned Initializer)
```powershell
# Create a Python virtual environment
python -m venv venv

# Activate the virtual environment (Windows PowerShell)
.\venv\Scripts\Activate.ps1

# Activate the virtual environment (Linux/macOS)
# source venv/bin/activate

# Upgrade package management tools
python -m pip install --upgrade pip
```

### 3. Frontend Environment Setup (Planned Initializer)
```bash
# Navigate to the frontend directory once scaffolded
cd frontend
npm install
```

### 4. Environment Variables Configuration
Create a `.env` file in the root/backend directory based on `.env.example`:
```env
# Application Settings
ENVIRONMENT=development
LOG_LEVEL=INFO

# Database Connection (Placeholder)
DATABASE_URL=postgresql://user:password@localhost:5432/govcontinue_db

# Document Storage (Local or S3 compatible)
STORAGE_BUCKET=govcontinue-documents
```

> [!WARNING]
> **Security Guardrail**: Never commit real database credentials, API keys, or operational secrets to public repositories.

---

## 10. How to Run (Development)

Once the application service packages are scaffolded, start the local development services:

### Start Backend API
```powershell
# From the backend directory with virtual environment activated:
uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
```
- Interactive Swagger Documentation: `http://127.0.0.1:8000/docs`

### Start Frontend Dashboard
```bash
# From the frontend directory:
npm run dev
```
- Web Application: `http://localhost:3000`

---

## 11. Security, RBAC & Governance

Because government records contain sensitive administrative files and citizen details, security principles are embedded at the design level:

1. **Principle of Least Privilege**: Users access only records explicitly assigned to their department and current project roles.
2. **Pre-Retrieval Authorization Filter**: Unlike standard RAG systems that query the full index, GovContinue verifies permissions **before** initiating database or vector searches. Unauthorized files are never fetched into memory.
3. **Data Boundary & Synthetic Datasets**: Real government records are never transmitted to unapproved public APIs. Prototype testing strictly utilizes internally consistent synthetic datasets.
4. **Defensive Prompt Separation**: Ingested records are treated strictly as passive text data rather than executable instructions, preventing prompt injection attacks.
5. **Human-in-the-Loop Decision Boundary**: The system assists incoming officers by presenting structured facts and evidence; it cannot independently approve budgets, modify contracts, or issue official orders.
6. **Regulatory Alignment**: Designed to respect CERT-In Information Security Guidelines and the data protection principles of India's Digital Personal Data Protection (DPDP) Act, 2023 / Rules 2025.

---

## 12. Current Project Status

| Milestone | Status | Description |
| :--- | :---: | :--- |
| **Problem Formulation & Research** | Completed | Validated against official administrative office procedures and transition challenges. |
| **Architectural & System Design** | Completed | MCA SAPM Design Levels documented (Architectural, High-Level, Data, Interface, Component). |
| **Synthetic Dataset Schema** | In Progress | Synthetic data specifications for Public Works Department handover scenarios. |
| **Backend REST API** | Planned | FastAPI application scaffolding, database models, and authentication endpoints. |
| **Knowledge & RAG Engine** | Planned | Relational timeline synthesis, vector retrieval, and citation verification pipelines. |
| **Frontend Officer Dashboard** | Planned | Next.js interface for handover brief, interactive timeline, and query screens. |
| **Production Deployment** | Planned | Requires departmental governance, security audit, and formal deployment approvals. |

---

## 13. Future Scope & Roadmap

- **Multi-Department Expansion**: Expanding beyond municipal and public works records into education, public health, and revenue departments.
- **Dedicated Graph Database**: Migrating relational link tables to Neo4j or Amazon Neptune as entity relationships scale.
- **Cross-Project Institutional Learning**: Detecting systemic failure modes and recurring contractor delays across multiple independent initiatives.
- **Air-Gapped Deployment**: Packaging lightweight open-weights LLMs for secure deployment inside isolated departmental data centers.
- **Official e-Office Integration**: Developing connectors to ingest authorized exports directly from government digital filing systems.

---

## 14. Contributors

- **Project Author**: Devanshu ([@devanshu-k09](https://github.com/devanshu-k09))
- **Academic Context**: Smart India Hackathon (SIH 2026) & MCA Semester 3 (Software Architecture & Project Management - SAPM)

*(Contributions, bug reports, and suggestions are welcome. Please open an issue or pull request.)*

---

## 15. License

*No license has been specified for this project. All rights are reserved by the project author. A standard open-source or academic evaluation license will be designated upon prototype release.*
