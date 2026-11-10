# Anton Korneev

**ML / NLP Engineer** (ex-Frontend) · PyTorch · HF Transformers · Agentic RAG · LoRA

+7 993 465 45 10 · telegram: @ankornlog · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

Engineer with 9 years of commercial development experience; for the past year I have specialized in LLM applications. I build systems from data preparation and model training to deployment. Focus — agentic RAG: retrieval, tool calling, streaming, memory, MCP. Delivered two projects: cross-community search with trained retriever and reranker and an LLM agent on top of them, as well as a trained multimodal summarizer with in-browser inference. Looking for an ML/NLP Engineer position with a focus on LLM agents.

---

## Projects

### arcanumchat — agentic RAG over a cross-community corpus for the Arcanum universe

_LangChain · MCP · PyTorch · sentence-transformers · BAAI/bge-m3 · BAAI/bge-reranker-v2-m3 · Qwen 3.6 35B · pgvector/Supabase · HF Spaces · vLLM · FastAPI · Docker_

[app](https://ankorn.github.io/arcanumchat/) · [code](https://github.com/ankorn/arcanumsearch)

- Implemented scraping of documents from heterogeneous sources (arcanum wiki, Reddit threads, patch and mod descriptions), removed aggregator documents, applied structural document chunking by wiki sections, normalized threads
- Built inference on vLLM and generated synthetic queries [dataset](https://huggingface.co/datasets/pameydorke/arcanumchat-cross-platform-with-vague-queries-qwen-36-a3b-fp8) with Qwen3.6-35B-A3B-FP8 on NVIDIA A100 80GB
- Manually wrote and labeled 200 queries for evaluation, implemented an evaluation algorithm using paired bootstrap over queries and confidence intervals
- Trained bi-encoder [bge-m3](https://huggingface.co/pameydorke/arcanumchat-retriever-bge-m3-v2) and cross-encoder [bge-reranker-v2-m3](https://huggingface.co/pameydorke/arcanumchat-reranker-bge-reranker-v2-m3-v2) on hard-negative datasets, obtained a [statistically significant improvement](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_eval.ipynb): **recall@10 0.90 -> 0.96** (95% CI [0.0260, 0.0990]); **ndcg@10: 0.79 -> 0.87** (95% CI [0.0406, 0.1170])
- Implemented hybrid search (dense + bm25, Reciprocal Rank Fusion) with a [statistically significant result](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_hybrid_search_eval.ipynb) **recall@5 0.90 -> 0.92** (95% CI [0.0052, 0.0417]) for 10 documents
- Deployed retriever and reranker to HF Spaces
- Stored embeddings in Supabase using pgvector, added a SQL KNN function and an edge function for searching and reranking relevant documents
- Wrote server-side agent logic using LangChain and FastAPI; streaming over WebSocket, memory via thread_id
- The agent is based on cloud-based Qwen3.6-35B-A3B via an OpenAI-compatible API; agent tools — retrieval pipeline and a math tool on an MCP server
- Deployed the server with Docker

<br/>

### redred — multimodal Reddit post summarizer running in the browser

_PyTorch · HF Transformers · Unsloth · Gemma 4 (multimodal) · LoRA · ONNX Runtime Web · WebGPU · Optimum · RAGAS_

[app](https://ankorn.github.io/redred/) · [code](https://github.com/ankorn/redred)

- Fine-tuned multimodal LLM gemma-4-E2B-it on mRedditSum with LoRA and Unsloth — **rougeLsum 0.29 → 0.32, rouge1 0.37 → 0.46**
- The model, quantized to 4 bits, runs with WebGPU and weighs 3.5GB
- Built an evaluation pipeline on RAGAS with Qwen3-4B-Instruct as LLM-as-judge
- Set up browser inference with ONNX Runtime Web and streaming generation
- Implemented Reddit thread and image scraping using Yandex Cloud Functions

---

## Skills

**ML / NLP**
Agentic RAG · Text classification · language modeling · seq2seq · attention · transformers · transfer learning · LLM · PEFT/LoRA · RLHF · quantization · retrieval

**Model Training**
Dense retrieval, contrastive learning (MultipleNegativesRankingLoss, GISTEmbedLoss), hard negative mining · fine-tuning multimodal LLMs · overfitting diagnostics · synthetic data generation via LLM

**Metrics**
recall@k · ndcg@k · ROUGE (rouge1, rougeLsum) · paired bootstrap · confidence intervals · RAGAS (SummaryScore, SemanticSimilarity)

**Inference / MLOps**
Docker · ONNX / Optimum, quantization (q4/q8), browser inference (ONNX Runtime Web) · vector search (pgvector, KNN) · deployment to HF Spaces, Supabase Edge Functions, Yandex Cloud Functions

**Stack**
Python, PyTorch, HF Transformers/Datasets/PEFT, Unsloth, sentence-transformers · LangChain

**Education**
NLP course at Yandex School of Data Analysis ([fork with solutions](https://github.com/ankorn/nlp_course)) — trained models on all topics · NLP Course For You · ML Crash Course · Deep Learning Specialization (Andrew Ng)

---

## Work Experience

### T-Bank — Frontend Engineer · 2023–2026

- Set up monitoring of process and product metrics (using Grafana), availability indicators and alerting for microfrontends
- Independently shipped three products to production in the microfrontend architecture of the personal account
- Led the algorithms section of technical interviews for a year; mentored an intern to a junior position

### Fibbee — Frontend Engineer (startup) · 2021–2023

- Sole frontend developer: built the product from scratch (React, TypeScript, Redux Toolkit)

### Altarix — Frontend Engineer · 2017–2021

- Moscow Electronic School: optimized initial page load by 20%
- DOM.RF: simplified the stack, reducing logic development time by 30% (React Query)
- Taught an internal JS course, mentored junior developers

---

## Additional

- **English:** C1