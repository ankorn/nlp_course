# Anton Korneev

**ML / NLP Engineer** (ex-Frontend) · PyTorch · HF Transformers · Agentic RAG · LoRA

+7 993 465 45 10 · tg: @ankornlog · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

Engineer with 9 years of commercial development experience. A year ago, I passed the ML/NLP assessment at T-Bank with a **junior+** result, and then completed two projects: a cross-community search system with a fine-tuned retriever and reranker, plus an LLM agent built on top of them, and a fine-tuned multimodal summarizer running inference in the browser. I build LLM applications end-to-end, from data preparation and model training to deployment. My focus is agentic RAG: retrieval, tool calling, streaming, memory, MCP. I'm looking for an ML/NLP Engineer position with an emphasis on LLM agents.

---

## Projects

### arcanumchat — agentic RAG over a cross-community corpus from the Arcanum universe

_LangChain · MCP · PyTorch · sentence-transformers · BAAI/bge-m3 · BAAI/bge-reranker-v2-m3 · Qwen 3.6 35B · pgvector/Supabase · HF Spaces · vLLM · FastAPI · Docker_

[app](https://ankorn.github.io/arcanumchat/) · [code](https://github.com/ankorn/arcanumsearch)

- Scraped over 1,000 documents from heterogeneous sources (Arcanum wiki, Reddit threads, patch and mod descriptions), removed aggregator documents, applied structural document chunking by wiki sections, normalized threads
- Deployed Qwen3.6-35B-A3B-FP8 inference on vLLM and generated a [dataset](https://huggingface.co/datasets/pameydorke/arcanumchat-cross-platform-with-vague-queries-qwen-36-a3b-fp8) of synthetic queries; ran on NVIDIA A100 80GB
- Wrote and annotated 200 evaluation queries by hand, implemented an evaluation algorithm using pairwise bootstrap over queries with confidence intervals
- Fine-tuned the bi-encoder [bge-m3](https://huggingface.co/pameydorke/arcanumchat-retriever-bge-m3-v2) and the cross-encoder [bge-reranker-v2-m3](https://huggingface.co/pameydorke/arcanumchat-reranker-bge-reranker-v2-m3-v2) on hard-negative datasets, achieving a [statistically significant improvement](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_eval.ipynb): **recall@10 0.90 -&gt; 0.96** (95% CI [0.0260, 0.0990]); **ndcg@10: 0.79 -&gt; 0.87** (95% CI [0.0406, 0.1170])
- Implemented hybrid search (dense + BM25, Reciprocal Rank Fusion) with a [statistically significant result](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_hybrid_search_eval.ipynb) of **recall@5 0.90 -&gt; 0.92** (95% CI [0.0052, 0.0417]) for 10 candidates
- Deployed the retriever and reranker on HF Spaces
- Stored embeddings in Supabase with pgvector, added a SQL KNN function and an edge function for searching and re-ranking relevant documents
- Wrote the agent's server-side logic using LangChain and FastAPI; streaming over WebSocket, memory via thread_id
- The agent runs on a cloud-hosted Qwen3.6-35B-A3B via an OpenAI-compatible API; the agent's tools are the retrieval pipeline and a math tool served by an MCP server
- Deployed the server with Docker

<br/>

### redred — multimodal Reddit post summarizer running in the browser

_PyTorch · HF Transformers · Unsloth · Gemma 4 (multimodal) · LoRA · ONNX Runtime Web · WebGPU · Optimum · RAGAS_

[app](https://ankorn.github.io/redred/) · [code](https://github.com/ankorn/redred)

- Fine-tuned the multimodal LLM gemma-4-E2B-it on mRedditSum using LoRA and Unsloth — **rougeLsum 0.29 -&gt; 0.32, rouge1 0.37 -&gt; 0.46**
- The model, quantized to 4 bits, runs via WebGPU and weighs 3.5GB
- Built an evaluation pipeline on RAGAS with Qwen3-4B-Instruct as the LLM-as-judge
- Set up browser inference with ONNX Runtime Web and streaming generation
- Implemented Reddit thread and image scraping using Yandex Cloud Functions

---

## Assessment

Passed the ML/NLP assessment process at T-Bank across sections: algorithms — senior-; classical ML — junior+; NLP — junior+. Overall grade based on section results — junior+

---

## Skills

**ML / NLP**
Agentic RAG · text classification · language modeling · seq2seq · attention · transformers · transfer learning · LLM · PEFT/LoRA · quantization · retrieval

**Model Training**
Dense retrieval, contrastive learning (MultipleNegativesRankingLoss, GISTEmbedLoss), hard negative mining · multimodal LLM fine-tuning · synthetic data generation via LLM

**Metrics**
recall@k · ndcg@k · ROUGE (rouge1, rougeLsum) · pairwise bootstrap · confidence intervals · RAGAS (SummaryScore, SemanticSimilarity)

**Inference / MLOps**
Docker · ONNX / Optimum, quantization (q4/q8), browser inference (ONNX Runtime Web) · vector search (pgvector, KNN) · deployment on HF Spaces, Supabase Edge Functions, Yandex Cloud Functions

**Stack**
Python, PyTorch, HF Transformers/Datasets/PEFT, Unsloth, sentence-transformers · LangChain

**Education**
Yandex School of Data Analysis NLP course ([fork with solutions](https://github.com/ankorn/nlp_course)) — trained models on all topics · NLP Course For You

---

## Work Experience

### T-Bank — Frontend Engineer · 2023–2026

- Set up monitoring of process and product metrics (with Grafana), availability indicators, and alerting for microfrontends
- Independently launched three products in production in the personal account's microfrontend architecture
- Led the algorithms section of technical interviews for a year; mentored an intern up to a junior position

### Fibbee — Frontend Engineer (startup) · 2021–2023

- Sole frontend developer: built the product from scratch (React, TypeScript, Redux Toolkit)

### Altarix — Frontend Engineer · 2017–2021

- Moscow Electronic School: optimized initial page load time by 20%
- DOM.RF: simplified the stack, cutting logic development time by 30% (React Query)
- Ran an internal JS course, mentored junior developers

---

## Additional

- **English:** C1

---