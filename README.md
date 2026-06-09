# claude-skills

Personal Claude Code skills — reusable technique guides for AI-assisted development.

## Skills

### [`rag-system-architect`](./rag-system-architect/SKILL.md)

A skill that guides Claude to architect and build any production-grade RAG system. It diagnoses your data and requirements through a short interview (or by scanning your project files automatically), prescribes a technique stack, and generates a concrete implementation plan.

**Phases:**
1. **Diagnose** — auto-detect your data files, or answer 5 questions about your data type, volume, query patterns, and constraints
2. **Prescribe** — recommends techniques across 4 layers: chunking, query enhancement, retrieval, and evaluation
3. **Implement** — generates a full implementation plan with file structure, component breakdown, and framework mappings

**Supported techniques:** 37 production RAG techniques across chunking, query enhancement, retrieval, and evaluation layers. See [`technique-matrix.md`](./rag-system-architect/technique-matrix.md) for the full reference.

## Credits

The RAG techniques referenced in this skill are sourced from:

**[NirDiamant/RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques)** by [Nir Diamant](https://github.com/NirDiamant)

> A comprehensive collection of advanced Retrieval-Augmented Generation (RAG) techniques, implemented as Jupyter notebooks with LangChain and LlamaIndex. Covers 37+ techniques from foundational to advanced architectures including Graph RAG, RAPTOR, Self-RAG, CRAG, and more.

All notebook links in this skill point directly to that repository. Full credit to Nir Diamant and contributors for the original implementations.

## Usage

These skills are loaded automatically by Claude Code from `~/.claude/skills/`. Invoke with `/rag-system-architect` or Claude will load the skill automatically when you mention RAG, vector search, document QA, semantic search, or similar topics.
