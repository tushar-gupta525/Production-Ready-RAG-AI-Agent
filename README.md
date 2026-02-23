# Production-Ready-RAG-AI-Agent
A production-ready, fully local Retrieval-Augmented Generation (RAG) AI agent using FastAPI, Inngest, Qdrant, Ollama, and Streamlit. Supports PDF ingestion, semantic search, and local LLM-based question answering without paid APIs.

# 🚀 Production-Ready RAG AI Agent (Event-Driven Backend)

A fully local, production-style Retrieval-Augmented Generation (RAG) backend built using an event-driven architecture.

This project demonstrates how to build a real-world RAG pipeline using:

- Inngest (event orchestration)
- FastAPI (backend integration)
- Qdrant (vector database)
- SentenceTransformers (local embeddings)
- Ollama (local LLM)

No paid APIs.  
No OpenAI dependency.  
No frontend required.

---

## 🧠 What This Project Does

1. Ingests PDF documents
2. Splits them into semantic chunks
3. Generates embeddings locally
4. Stores vectors in Qdrant
5. Accepts natural language questions
6. Retrieves relevant context
7. Generates answers using a local LLM (LLaMA 3 via Ollama)

All workflows are executed and monitored directly from the **Inngest Dev Server UI**.

---

## 🏗️ Architecture Overview

Manual Trigger (Inngest Dev UI)
        ↓
Inngest Event
        ↓
FastAPI + Inngest Function
        ↓
PDF Chunking
        ↓
Local Embeddings (SentenceTransformers)
        ↓
Qdrant Vector Storage
        ↓
Semantic Retrieval  
        ↓
Ollama (Local LLM)
        ↓
Answer Returned in Run Output


This architecture separates:
- Orchestration
- Retrieval
- Generation
- Infrastructure

It follows real production backend patterns.

---

## 🛠 Tech Stack

- Python
- FastAPI
- Inngest
- Qdrant
- SentenceTransformers
- Ollama (LLaMA 3)
- Docker

---

## ▶️ How to Run (Local Setup)

### 1️⃣ Start Qdrant (Vector DB)

docker run -d --name qdrantRagDb -p 6333:6333 qdrant/qdrant

### 2️⃣ Start Ollama and pull model
ollama pull llama3
ollama run llama3

### 3️⃣ Start Backend (FastAPI + Inngest)
uv run --active uvicorn main:app

### 4️⃣ Start Inngest Dev Server
npx inngest-cli@latest dev -u http://127.0.0.1:8000/api/inngest --no-discovery

### 🧪 How to Use
1. 📄 Ingest a PDF

  - In Inngest Dev UI:
  - Go to Functions
  - Select RAG: Ingest PDF
  - Invoke with:
    pass the "pdf_path" : "path to your pdf"

### 2.❓ Query the PDF
  - In Inngest Dev UI:
  - Select RAG: Query PDF
   - Invoke with:
     pass the question "question": "any question like - what is this document about?"
  - The generated answer will appear in the run output. 
