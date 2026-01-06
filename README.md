# RAG_project

Lightweight Retrieval-Augmented Generation (RAG) pipeline: ingest documents, build a vector index, and augment a generative model with retrieved context for accurate, explainable responses.

## Quick Start
Requirements: Python 3.10+, pip (or poetry), optional Docker. Store service API keys in a `.env` file.

Clone and install:
```bash
git clone https://github.com/Seetureddy/RAG_project.git
cd RAG_project
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Example `.env`:
```
OPENAI_API_KEY=sk-...
VECTOR_STORE=faiss
EMBEDDING_MODEL=openai-text-embedding-3
LLM_MODEL=gpt-4o
```

## Common Commands
Index documents:
```bash
python -m rag_project.ingest --source-dir data/source --index-name my-corpus
```
Query an index:
```bash
python -m rag_project.query --index-name my-corpus --query "What are the benefits of RAG?"
```
Run API server:
```bash
uvicorn rag_project.server:app --host 0.0.0.0 --port 8000
```

## Architecture (1-line)
Documents → chunking → embeddings → vector store → retrieve k-nearest → LLM generation with assembled context.

## Supported (examples)
- Vector stores: FAISS (local), Pinecone, Milvus (adapters)
- Embeddings/LLMs: OpenAI + Hugging Face adapters
- Parsers: PDF, DOCX, Markdown, text

## Testing & Deployment
Run tests:
```bash
pytest -q
```
Docker:
```bash
docker build -t rag_project:latest .
docker run --env-file .env -p 8000:8000 rag_project:latest
```

## Contributing & License
Contributions welcome—please open issues/PRs. Licensed under MIT (see LICENSE).

Maintainer: Seetureddy — https://github.com/Seetureddy/RAG_project
