# 🧠 Neural RAG Interface

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-00a393.svg)
![Groq](https://img.shields.io/badge/Groq-Powered-f55036.svg)
![FAISS](https://img.shields.io/badge/FAISS-Vector_Search-blueviolet.svg)

A lightweight, custom-built Retrieval-Augmented Generation (RAG) pipeline and interactive API set, built completely from scratch. 

This project demonstrates a deep understanding of the core concepts of RAG by stripping away heavy orchestration frameworks (like LangChain or LlamaIndex). It implements the full ingestion-retrieval-generation cycle natively using **Sentence Transformers** for local embeddings, **FAISS** for vector similarity search, and **Groq's hyper-fast inference API** for generation.

---

## ✨ Features

* **From-Scratch Architecture:** Explicit, modular implementation of ingestion, retrieval, and generation steps.
* **Local Embeddings:** Utilizes `all-MiniLM-L6-v2` to compute dense vector representations locally, ensuring privacy and zero API latency for the embedding phase.
* **Vector Database:** Integrates `FAISS` (Facebook AI Similarity Search) for high-performance, scalable semantic search.
* **Blazing Fast LLM Inference:** Powered by Groq's API with the `llama-3.3-70b-versatile` model, delivering near-instantaneous reasoning and answer generation.
* **FastAPI Backend:** A clean, RESTful Python API exposing the RAG capabilities for external integrations.
* **Cyberpunk Aesthetics:** Includes assets for a stunning, custom dark-themed UI with glassmorphism and neon accents.

## 🏗️ Core Components

* `app.py`: The FastAPI application that orchestrates the RAG components and exposes the `/chat` endpoint.
* `ingest.py`: Reads the knowledge base (`data/sample.txt`), chunks the text, computes text embeddings, and indexes them into a FAISS vector store.
* `retrieve.py`: Vectorizes the user's query and performs a nearest-neighbor search against the FAISS index to fetch the most relevant context.
* `generate.py`: Constructs an augmented prompt and calls the Groq API (via the OpenAI client structure) to generate the final, context-aware answer.
* `main.py`: A CLI alternative for running the RAG pipeline directly from the terminal.

## 🚀 Getting Started

### Prerequisites

* Python 3.9+
* A Groq API Key

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/rag-from-scratch.git
   cd rag-from-scratch
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Configure your API key. Make sure your Groq API key is present in `generate.py` or securely loaded via a `.env` file depending on your configuration.

### Running the API

Start the FastAPI application using Uvicorn:

```bash
uvicorn app:app --reload --port 8004
```

The API will be live at `http://127.0.0.1:8004`. 

### API Endpoints

* **GET `/`**: Health check. Returns API status.
* **POST `/chat`**: Main RAG endpoint.
  * **Payload:** `{"question": "Your query here"}`
  * **Response:** Returns the user question, the retrieved document strings, and the synthesized LLM answer.

## 🛠️ Tech Stack

* **Backend:** FastAPI, Python
* **Machine Learning:** SentenceTransformers, FAISS, Numpy
* **LLM Provider:** Groq (llama-3.3-70b-versatile)
* **Frontend UI (Optional):** Vanilla HTML, CSS, JavaScript

## 🔮 Future Enhancements

* Implement dynamic document uploads and on-the-fly vector indexing.
* Add advanced chunking strategies (e.g., semantic chunking or overlapping windows).
* Integrate conversational memory (chat history) for multi-turn interactions.
* Implement hybrid search (Keyword + Vector) for improved retrieval accuracy.

---
*Crafted for maximum performance and educational clarity.*
