# Retrieval-Augmented Generation (RAG) Pipeline

My hands-on work on Retrieval-Augmented Generation: building a RAG pipeline over PDF research papers first from scratch, then with LangChain, using Chroma, local HuggingFace embeddings (`all-mpnet-base-v2`) and a Groq-hosted `gpt-oss` model.

## Contents

| File / Folder | Description |
|---|---|
| [1_rag_concepts.md](1_rag_concepts.md) | Notes on what RAG is, RAG vs fine-tuning, key components and evaluation. |
| [2_rag_from_scratch.ipynb](2_rag_from_scratch.ipynb) | Full RAG pipeline built by hand with no framework. |
| [3_rag_from_scratch_exercise.ipynb](3_rag_from_scratch_exercise.ipynb) | Convert and clean a PDF with MarkItDown, then measure the effect of cleaning on retrieval and answers (including an LLM judge). |
| [4_rag-pipeline-gpt-oss.ipynb](4_rag-pipeline-gpt-oss.ipynb) | The same pipeline with LangChain, Chroma and Groq `gpt-oss`. |
| [5_rag_exercise_notebook.ipynb](5_rag_exercise_notebook.ipynb) | Source citations, tuning the number of retrieved chunks, and LLM-as-judge evaluation. |
| [6_rag_real_world_applications.md](6_rag_real_world_applications.md) | RAG use cases across industries. |
| [documents/](documents/) | Sample PDFs used by the notebooks. |
| [assets/](assets/) | Workflow diagrams. |

All notebooks have been executed once and are saved with their outputs.

## Key findings

- Cleaning the MarkItDown output (page headers, page numbers, short lines) raised the mean retrieval score from 0.510 to 0.559 and changed every retrieved chunk.
- With small chunks, retrieving 6 chunks instead of 2 improved judged faithfulness from 3 to 5 out of 5.

## Setup

```bash
uv sync
cp .env.example .env   # then set GROQ_API_KEY
```

Requires Python 3.13 and a free Groq API key. The embedding model (~400 MB) downloads on first run. Never commit `.env`.
