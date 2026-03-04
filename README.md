# Azure Multi-Modal Compliance Orchestration Engine

An **AI-powered video compliance auditing system** built using **LangGraph, LangSmith, and Azure AI services**.  
The system analyzes multimedia content (video transcripts + OCR text) and checks it against regulatory compliance rules using a **Retrieval-Augmented Generation (RAG)** architecture.

This project demonstrates how **multi-agent AI orchestration** can automate compliance verification pipelines for media and marketing content.

---

# Features

- **Multimodal Video Processing**
  - Uses **Azure Video Indexer** to extract transcripts and OCR text from video content.

- **AI-powered Compliance Reasoning**
  - Uses **Azure OpenAI GPT-4o** for contextual reasoning.

- **Retrieval Augmented Generation (RAG)**
  - Compliance rules stored in **Azure AI Search**
  - Retrieved using **OpenAI embeddings**

- **LangGraph Workflow**
  - Orchestrates a multi-step compliance pipeline with modular reasoning nodes.

- **Observability**
  - Full tracing using **LangSmith**
  - System monitoring via **Azure Application Insights**

---

# Architecture Overview

## Architecture Flow

<img width="1238" height="623" alt="Screenshot 2026-03-04 at 9 22 54 AM" src="https://github.com/user-attachments/assets/2a6fc0f9-1eb2-4f49-96e3-09b0e39dac92" />

```
Video Upload
↓
Azure Video Indexer
↓
Transcript + OCR Extraction
↓
Azure AI Search (Compliance Knowledge Base)
↓
LangGraph Orchestration Pipeline
↓
Azure OpenAI (GPT-4o Reasoning)
↓
Compliance Violation Detection
↓
Compliance Report Generation
```

---

# 🛠 Tech Stack

| Component | Technology |
|-----------|------------|
| LLM | Azure OpenAI (GPT-4o) |
| Embeddings | text-embedding-3-small |
| Orchestration | LangGraph |
| Tracing | LangSmith |
| Video Processing | Azure Video Indexer |
| Knowledge Retrieval | Azure AI Search |
| Storage | Azure Blob Storage |
| Monitoring | Azure Application Insights |
| Backend | FastAPI |
| Server | Uvicorn |
| Environment Manager | uv |

---

# Installation

### Clone the Repository

```bash
git clone https://github.com/KartikSuryavanshi/Azure-Multi-Modal-Compliance-Orchestration-Engine-using-LangGraph-and-LangSmith.git
```
---

### Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate
```

---

### Install Dependencies

Since this project uses **pyproject.toml**, install dependencies with:

```bash
pip install -e .
```

Or install directly:

```bash
pip install -r requirements.txt
```

---

# Environment Configuration

Create a `.env` file in the root directory.

```bash
cp .env.example .env
```

Add the following variables:

```env
# Azure Storage
AZURE_STORAGE_CONNECTION_STRING=""

# Azure OpenAI
AZURE_OPENAI_API_KEY=""
AZURE_OPENAI_ENDPOINT=""
AZURE_OPENAI_API_VERSION="2024-12-01-preview"
AZURE_OPENAI_CHAT_DEPLOYMENT="gpt-4o"

# Embedding Model
AZURE_OPENAI_EMBEDDING_DEPLOYMENT="text-embedding-3-small"

# Azure AI Search
AZURE_SEARCH_ENDPOINT=""
AZURE_SEARCH_API_KEY=""
AZURE_SEARCH_INDEX_NAME="brand-compliance-rules"

# Azure Video Indexer
AZURE_VI_NAME=""
AZURE_VI_LOCATION="eastus"
AZURE_VI_ACCOUNT_ID=""
AZURE_SUBSCRIPTION_ID=""
AZURE_RESOURCE_GROUP=""
AZURE_TENANT_ID=""

# Azure Monitoring
APPLICATION_INSIGHTS_CONNECTION_STRING=""

# LangSmith
LANGCHAIN_TRACING_V2=true
LANGSMITH_ENDPOINT="https://api.smith.langchain.com"
LANGSMITH_API_KEY=""
LANGSMITH_PROJECT="brand-guardian-prod"
```

**Important**

Never commit `.env` to GitHub.  
Make sure `.env` is included in `.gitignore`.

---

# Running the Server

Start the backend API using **Uvicorn**

```bash
uv run uvicorn backend.src.api.server:app --reload
```

### What this command does

| Part | Description |
|-----|-------------|
| `uv run` | Runs the command inside the uv environment |
| `uvicorn` | ASGI server for FastAPI |
| `backend.src.api.server:app` | Points to the FastAPI app |
| `--reload` | Automatically reloads server when code changes |

---

# 🌐 Access the API

After starting the server open:

```
http://127.0.0.1:8000
```

### Interactive API Docs

Swagger UI

```
http://127.0.0.1:8000/docs
```

ReDoc

```
http://127.0.0.1:8000/redoc
```

---

# 🔄 LangGraph Compliance Pipeline

The system uses **LangGraph state orchestration** to manage the AI workflow.

```
Video Processing Node
↓
Compliance Rule Retrieval Node
↓
Violation Detection Node
↓
Report Generation Node
```

Each node represents an **agent responsible for a specific reasoning task**.

---

# Example Compliance Output

<img width="1399" height="786" alt="Screenshot 2026-03-04 at 9 16 00 AM" src="https://github.com/user-attachments/assets/a5def7e4-4496-4ed7-87ab-5621404449e9" />


# Observability dashboard LangSmith

(Link - https://smith.langchain.com/o/82e4987c-f9c4-43fe-9e5e-e3fd70b1c645/projects/p/f88a2d6b-3cc7-468f-b058-8cd6d00e199a?timeModel=%7B%22duration%22%3A%221d%22%7D&peek=019cb6d5-33ac-7b03-93eb-55416c25cbf3&peeked_trace=019cb6d5-33ac-7b03-93eb-55416c25cbf3)

<img width="1440" height="786" alt="Screenshot 2026-03-04 at 9 18 31 AM" src="https://github.com/user-attachments/assets/a44f6982-fc21-42ca-9515-ebd96ed3e430" />

# Azure Application Insights


![WhatsApp Image 2026-03-04 at 9 00 40 AM](https://github.com/user-attachments/assets/a6f87baa-c2d5-4df2-8d98-4c8b3e937c5c)




---
