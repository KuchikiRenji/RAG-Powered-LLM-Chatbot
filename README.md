# RAG-Powered LLM Chatbot | Document QA with Retrieval-Augmented Generation

**Build a multi-source document chatbot with RAG (Retrieval-Augmented Generation), LangChain, and LLMs. Query your PDFs and text files with AI-powered, context-aware answers.**

---

## What is this project?

A **RAG-based (Retrieval-Augmented Generation) chatbot** that lets you upload PDF and text documents as a knowledge base and ask questions in natural language. The system retrieves relevant chunks from your documents and uses a large language model (LLM) to generate accurate, cited answers—ideal for document Q&A, internal knowledge bases, and policy handbooks.

**Tech stack:** Python · LangChain · FAISS · Streamlit · Hugging Face (sentence-transformers, optional LLM APIs) · PyTorch

---

## Table of Contents

- [Features](#features)
- [How It Works](#how-it-works)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running the Chatbot](#running-the-chatbot)
- [RAG Evaluation Pipeline](#rag-evaluation-pipeline)
- [Project Structure](#project-structure)
- [Author & Contact](#author--contact)
- [License](#license)

---

## Features

- **Multi-source RAG:** Use multiple PDF and text files as a single searchable knowledge base.
- **Document embedding UI:** Upload documents, chunk them, and build FAISS vector stores via Streamlit.
- **Conversational chatbot:** Chat with memory; answers are grounded in your uploaded documents.
- **Configurable:** Choose vector store, temperature, max length, and embedding/LLM models (e.g. Hugging Face).
- **Optional dev container:** Consistent dev environment with VS Code Remote Containers.

---

## How It Works

1. **Document ingestion:** PDFs and text files are loaded, split into chunks (e.g. with `RecursiveCharacterTextSplitter`), and embedded.
2. **Vector store:** Embeddings are stored in a FAISS index for fast similarity search.
3. **Retrieval:** Your question is embedded; the top-k most similar chunks are retrieved from the vector store.
4. **Generation:** Retrieved context + your question are sent to an LLM (e.g. via Hugging Face) to produce a final answer.

So: **retrieval** (from your docs) + **generation** (from the LLM) = **RAG**.

### High-level flow

- **Without RAG:** LLM answers only from its training data.
- **With RAG:** LLM is augmented with your documents, so answers are grounded in your content and stay up to date.

*(You can add your own architecture/flow diagrams here; use descriptive alt text for SEO, e.g. "RAG chatbot architecture: documents → embedding → FAISS → retrieval → LLM → answer.")*

---

## Prerequisites

- **Python 3.8+**
- **pip**
- (Optional) **Hugging Face API key** if using Hugging Face Hub LLMs
- (Optional) **CUDA-capable GPU** for faster embeddings/LLM inference

---

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/KuchikiRenji/RAG-Powered-LLM-Chatbot.git
   cd RAG-Powered-LLM-Chatbot
   ```

2. **Create a virtual environment (recommended)**

   ```bash
   python -m venv venv
   source venv/bin/activate   # Linux/macOS
   # or: venv\Scripts\activate   # Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Environment variables (optional)**

   Create a `.env` file in the project root if you use Hugging Face:

   ```
   API_KEY=your_hugging_face_token
   ```

---

## Running the Chatbot

1. **Start the Streamlit app**

   ```bash
   streamlit run chatbot_streamlit_combined.py
   ```

2. **Document embedding**
   - In the sidebar, open **Document Embedding**.
   - Upload PDF or text files, set chunk size/overlap if needed, and build or update a vector store (saved under `vector store/`).

3. **Chat**
   - Switch to **RAG Chatbot** in the sidebar.
   - Select your vector store, set model options (e.g. temperature, max length), and start asking questions. Answers are based on your uploaded documents.

### Development container (optional)

- Install [VS Code](https://code.visualstudio.com/) and the **Remote - Containers** extension.
- Open the project folder, press `F1` → **Remote-Containers: Reopen in Container**.

---

## RAG Evaluation Pipeline

The project includes an evaluation perspective for RAG quality:

1. **Data preparation:** Documents as knowledge base; a set of representative queries.
2. **Embedding & indexing:** Documents → embeddings → FAISS index.
3. **Retrieval:** Query → embedding → similarity search → top-k chunks.
4. **Generation:** Chunks + query → LLM → response.
5. **Metrics:** Accuracy, relevance, fluency, and user satisfaction.
6. **Iteration:** Error analysis, tuning (e.g. chunk size, model choice), and re-evaluation.

Improvements can come from: more/diverse documents, better retrieval (embeddings, chunking), optional model fine-tuning, and iterative testing with user feedback.

---

## Project Structure

```
RAG-Powered-LLM-Chatbot/
├── chatbot_streamlit_combined.py   # Streamlit UI: embedding + chatbot
├── falcon.py                       # RAG logic: loaders, splitter, FAISS, chain
├── requirements.txt
├── Document-pdfs/                  # Example/sample documents
├── vector store/                   # FAISS indices (created at runtime)
└── devcontainer/                   # VS Code dev container config
```

---

## Author & Contact

**KuchikiRenji**

- **GitHub:** [github.com/KuchikiRenji](https://github.com/KuchikiRenji)
- **Email:** KuchikiRenji@outlook.com
- **Discord:** kuchiki_renji

---

## License

See repository license file (if present). This project is for educational and portfolio use.

---

**Keywords:** RAG, retrieval augmented generation, LLM chatbot, document chatbot, PDF QA, LangChain, FAISS, Streamlit, Hugging Face, document Q&A, knowledge base chatbot.
