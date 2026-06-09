---
name: rag-system-architect
description: Use when building any RAG system — triggered by words like RAG, retrieval-augmented, vector search, document QA, embedding pipeline, semantic search, or "search over my documents/PDFs/data". Also use when user has documents and wants an AI that can answer questions about them.
---

# RAG System Architect

## Overview

Diagnose the user's data and requirements, prescribe a production-grade technique stack, then generate a concrete implementation plan. Framework-agnostic — works with LangChain, LlamaIndex, or raw code.

## Phase 1 — Diagnose

**Always open with:**
> "Want me to scan your project files and figure out the right RAG approach for you? Or would you prefer to describe your data yourself?"

### Auto-detect path (user says yes / is lazy)

1. Scan project for: `.pdf`, `.csv`, `.json`, `.txt`, `.md`, images, existing vector DB config, embedding code
2. Check available MCP connections (vector DB, SQL, graph DB)
3. Read a **sample only** — never modify any user data
4. Infer: data type, estimated volume, structure, likely query patterns
5. Present findings and wait for confirmation:
   > "I found [X files of type Y]. It looks like [description]. Based on this I'm going to recommend [brief stack summary]. Does this look right before I go deeper?"

### Manual path (user wants to describe)

Ask these one at a time — do not batch them:

1. **Data type** — PDFs, web pages, CSV/JSON, mixed, images/visual PDFs?
2. **Volume** — under 1K docs, 1K–100K, or 100K+?
3. **Query type** — factual lookups, multi-hop/comparison, summarization, conversational?
4. **Pain point** — missing relevant content, too much noise, wrong answers, slow performance?
5. **Constraints** — offline/local only, specific vector DB, existing embeddings, latency budget?

## Phase 2 — Prescribe

After diagnosis (and confirmation if auto-detect), prescribe a technique stack across 4 layers.

For each technique state: **what** it is, **why** it fits this specific case, and **the main trade-off**.

The 4 layers to always cover:
- **Chunking** — how to split and prepare documents
- **Query Enhancement** — how to improve query understanding
- **Retrieval** — how to find and rank the right content
- **Evaluation** — how to measure accuracy (always include at least one)

**Full technique reference:** See `technique-matrix.md` in this skill directory for all 37 techniques, selection rules, and notebook links.

### Quick selection shortcuts

| Data type | Start with |
|---|---|
| PDFs with headers/sections | Contextual Chunk Headers + Hierarchical Indices |
| JSON/CSV structured data | JSON RAG + Fusion Retrieval |
| Images or visual PDFs | Multi-modal RAG (Captioning or ColPali) |
| Mixed / unknown | Semantic Chunking + Fusion Retrieval + Adaptive Retrieval |

| Query type | Add |
|---|---|
| Multi-hop / comparison | Graph RAG + RAPTOR + Query Decomposition |
| Vague / abstract | HyDE + Step-back Prompting |
| Conversational | MemoRAG |
| Mixed types | Adaptive Retrieval as router |

| Pain point | Add |
|---|---|
| Too much noise | Reranking + Contextual Compression + Dartboard |
| Missing content | Fusion Retrieval + Document Augmentation |
| Wrong answers | Self-RAG or CRAG |
| Large scale (100K+) | RAPTOR + Hierarchical Indices |

## Phase 3 — Implement

After user confirms the prescription, generate a full implementation plan with:

1. **Architecture** — text diagram of components and data flow
2. **File structure** — what to create and each file's responsibility
3. **Component breakdown** — each module's interface (inputs/outputs)
4. **Ordered tasks** — concrete, step-by-step, TDD-first
5. **Framework mapping** — how each technique maps to LangChain / LlamaIndex / raw Python
6. **Reference notebooks** — link each technique to its notebook:
   `https://github.com/NirDiamant/RAG_Techniques/blob/main/all_rag_techniques/<notebook>.ipynb`

## Rules

- Never modify user data — read-only during auto-detect
- Always confirm before generating the implementation plan
- Always include at least one evaluation technique
- Lazy path first — offer auto-detect before asking 5 questions
- Load `technique-matrix.md` when you need full technique details or notebook links
