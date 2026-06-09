# RAG Technique Matrix

All techniques from NirDiamant/RAG_Techniques.
Base URL: https://github.com/NirDiamant/RAG_Techniques/blob/main/all_rag_techniques/

## Chunking Layer

| Technique | When to use | Notebook |
|---|---|---|
| Semantic Chunking | Text with natural topic shifts; avoids mid-concept splits | semantic_chunking.ipynb |
| Proposition Chunking | Max precision; each chunk = one atomic fact | proposition_chunking.ipynb |
| Contextual Chunk Headers | Docs with clear sections/headings (reports, manuals) | contextual_chunk_headers.ipynb |
| JSON RAG | Structured JSON data; combine relevant fields for embedding | json_rag.ipynb |
| Chunk Size Optimization | Unknown optimal size; run experiments to find balance | choose_chunk_size.ipynb |
| Relevant Segment Extraction | Need multi-chunk context windows around best match | relevant_segment_extraction.ipynb |
| Context Window Enhancement | Need neighboring sentences around best sentence | context_enrichment_window_around_chunk.ipynb |
| Document Augmentation | Sparse docs; augment with LLM-generated questions | document_augmentation.ipynb |

## Query Enhancement Layer

| Technique | When to use | Notebook |
|---|---|---|
| HyDE (Hypothetical Document Embedding) | Query-document vocabulary mismatch; short queries vs long docs | HyDe_Hypothetical_Document_Embedding.ipynb |
| HyPE (Hypothetical Prompt Embeddings) | Anticipate question types at index time; question-question matching | HyPE_Hypothetical_Prompt_Embeddings.ipynb |
| Query Transformations | Vague queries; multi-hop questions; abstract questions needing step-back | query_transformations.ipynb |
| Adaptive Retrieval | Mixed query types in same system; classify then route | adaptive_retrieval.ipynb |

## Retrieval Layer

| Technique | When to use | Notebook |
|---|---|---|
| Fusion Retrieval | Combine keyword exact-match with semantic search for best of both | fusion_retrieval.ipynb |
| Reranking | Too many retrieved chunks; need to surface top-K accurately | reranking.ipynb |
| Multi-faceted Filtering | Need metadata/date/source filters alongside semantic search | multi_faceted_filtering.ipynb |
| Hierarchical Indices | Large corpora; two-tier: summaries for routing + chunks for retrieval | hierarchical_indices.ipynb |
| Dartboard Retrieval | Results too similar/redundant; optimize for relevance + diversity | dartboard.ipynb |
| Contextual Compression | Chunks contain too much noise; LLM-compress to relevant content | contextual_compression.ipynb |
| Self-RAG | System needs to decide when retrieval helps vs hurts | self_rag.ipynb |
| CRAG (Corrective RAG) | Retrieved docs may be irrelevant; fall back to web search | crag.ipynb |
| RAPTOR | Deep hierarchical docs; need recursive summarization tree | raptor.ipynb |
| Graph RAG (LangChain) | Entity/relationship questions; knowledge graph extraction | graph_rag.ipynb |
| Graph RAG (Milvus) | Multi-hop questions + vector search; relationship triplets | graphrag_with_milvus_vectordb.ipynb |
| Microsoft GraphRAG | Large corpus; community detection + bottom-up summarization | Microsoft_GraphRag.ipynb |
| Agentic RAG | Production pipeline; document parsing + reranking + grounded LLM | Agentic_RAG.ipynb |
| MemoRAG | Conversational; persistent key-value memory + surrogate queries | memorag.ipynb |
| Multi-modal RAG (Captioning) | PDFs/PPTs with images, charts, diagrams | multi_model_rag_with_captioning.ipynb |
| Multi-modal RAG (ColPali) | Visual-heavy docs; convert to images, retrieve with vision LLM | multi_model_rag_with_colpali.ipynb |

## Evaluation Layer

| Technique | When to use | Notebook |
|---|---|---|
| DeepEval | Correctness, faithfulness, contextual relevancy metrics | evaluation_deep_eval.ipynb |
| GROUSE | Six-metric contextually-grounded evaluation | evaluation_grouse.ipynb |
| End-to-End RAG Evaluation | Full pipeline eval with RAGAS + completeness + hallucination | end-2-end_rag_evaluation.ipynb |
| Open-RAG-Eval | UMBRELA scoring + citation/hallucination detection | open-rag-eval-example.ipynb |

## Selection Rules (by diagnosis signal)

| Signal | Prescribe |
|---|---|
| PDFs / docs with sections/headers | Contextual Chunk Headers + Hierarchical Indices + Fusion Retrieval |
| Structured JSON/CSV | JSON RAG + Fusion Retrieval + Multi-faceted Filtering |
| Images or visual PDFs | Multi-modal RAG (Captioning) or ColPali |
| Multi-hop / comparison questions | Graph RAG + RAPTOR + Query Transformations (decompose) |
| Vague / abstract queries | HyDE + Step-back Prompting |
| Too much noise in results | Reranking + Contextual Compression + Dartboard |
| Missing relevant content | Fusion Retrieval + Document Augmentation + HyPE |
| Large corpus (100K+ docs) | Hierarchical Indices + RAPTOR + Adaptive Retrieval |
| Needs self-correction / low confidence | Self-RAG or CRAG |
| Conversational / session memory | MemoRAG |
| Unknown query types (mixed) | Adaptive Retrieval as router |
| Need to validate accuracy | Always add DeepEval or End-to-End Evaluation |
