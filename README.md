# Azure Multi-Modal Compliance Orchestration Engine

An **AI-powered video compliance auditing system** built using **LangGraph, LangSmith, and Azure AI services**.  
The system analyzes multimedia content (video transcripts + OCR text) and checks it against regulatory compliance rules using a **Retrieval-Augmented Generation (RAG)** architecture.

This project demonstrates how **multi-agent AI orchestration** can automate compliance verification pipelines for media and marketing content.

---

# 🚀 Features

- 🎥 **Multimodal Video Processing**
  - Uses **Azure Video Indexer** to extract transcripts and OCR text from video content.

- 🧠 **AI-powered Compliance Reasoning**
  - Uses **Azure OpenAI GPT-4o** for contextual reasoning.

- 🔍 **Retrieval Augmented Generation (RAG)**
  - Compliance rules stored in **Azure AI Search**
  - Retrieved using **OpenAI embeddings**

- 🔄 **LangGraph Workflow**
  - Orchestrates a multi-step compliance pipeline with modular reasoning nodes.

- 📊 **Observability**
  - Full tracing using **LangSmith**
  - System monitoring via **Azure Application Insights**

---

# 🧱 Architecture Overview
## Architecture Flow

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

# ⚙️ Installation

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/compliance-engine.git
cd compliance-engine
```

---

### 2️⃣ Install Dependencies

Using **uv**

```bash
uv pip install -r requirements.txt
```

---

# 🔐 Environment Configuration

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

⚠️ **Important**

Never commit `.env` to GitHub.  
Make sure `.env` is included in `.gitignore`.

---

# ▶️ Running the Server

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

# 📊 Example Compliance Output

```
Video: marketing_campaign_01.mp4

Detected Issues:

1. Misleading promotional claim detected
2. Missing regulatory disclaimer
3. Non-compliant product statement

Risk Score: HIGH

Recommendation:
Update marketing message and add mandatory disclaimer.
```

---
