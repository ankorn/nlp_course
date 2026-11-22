---
---

---

# Anton Korneev

**ML/NLP Engineer** · NLP · LLM · LangChain · PyTorch · HF Transformers · Agentic RAG

+7 993 465 45 10 · telegram: @ankornlog · an.korn.zasekin@gmail.ru · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

A year ago, I passed the ML/NLP assessment at T-Bank with a **junior+** result and completed onboarding in the telephony team, and then implemented two of my own projects: cross-community search with fine-tuned Retriever/Reranker and an LLM agent, as well as multimodal summarization with a fine-tuned model. I build LLM applications from data preparation and model training to deployment. I am looking for an ML/NLP Engineer position.

---

## Projects

### arcanumchat — agentic RAG over cross-community search across the Arcanum universe

_PyTorch · sentence-transformers · LangChain · MCP · bge-m3 · bge-reranker-v2-m3 · Qwen3.6-35B-A3B · pgvector/Supabase · HF Spaces · vLLM · FastAPI · Docker_

[app](https://ankorn.github.io/arcanumchat/) · [code](https://github.com/ankorn/arcanumsearch)

- Improved RAG quality on a sample of 20 candidates: obtained a [statistically significant gain](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_eval.ipynb) of **recall@10 +6.7%** (recall@10 = 0.90 → recall@10 = 0.96) and **NDCG@10 +10.1%** (NDCG@10 = 0.79 → NDCG@10 = 0.87) (95% confidence interval of the gain [0.0260, 0.0990] and [0.0406, 0.1170], respectively). To achieve this, I fine-tuned the bi-encoder [bge-m3](https://huggingface.co/pameydorke/arcanumchat-retriever-bge-m3-v2) and the cross-encoder [bge-reranker-v2-m3](https://huggingface.co/pameydorke/arcanumchat-reranker-bge-reranker-v2-m3-v2) on hard-negative datasets; I assessed significance using paired bootstrap by query and confidence intervals
- Improved RAG quality on a sample of 10 candidates, obtaining a small but [statistically significant gain](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_hybrid_search_eval.ipynb) of **recall@5 +2.2%** (recall@5 = 0.90 → recall@5 = 0.92) (95% confidence interval [0.0052, 0.0417]): implemented hybrid dense + BM25 search and RRF; evaluated using paired bootstrap by query and confidence intervals
- Generated a [dataset](https://huggingface.co/datasets/pameydorke/arcanumchat-cross-platform-with-vague-queries-qwen-36-a3b-fp8) of 5,000 synthetic queries for RAG: launched Qwen3.6-35B-A3B-FP8 using vLLM on an NVIDIA A100 80GB, built the generation pipeline, wrote and tested prompts; the dataset was used to fine-tune retrieval models
- Implemented scraping of more than 1,000 documents from heterogeneous sources (arcanum wiki, Reddit threads, patch and mod descriptions), removed aggregator documents, applied structural chunking of documents by wiki sections, and normalized threads
- Deployed the retriever and reranker in HF Spaces; stored embeddings in Supabase using pgvector and added an SQL KNN function
- Wrote the server-side agent logic using LangChain and FastAPI; WebSocket streaming, memory using thread_id; deployed the server using Docker
- The agent is based on cloud Qwen3.6-35B-A3B via an OpenAI-compatible API; the agent tools are a retrieval pipeline and a math tool on an MCP server

### redred — multimodal summarizer for Reddit posts that runs in the browser

_PyTorch · HF Transformers · Unsloth · gemma-4-E2B-it (multimodal) · Qwen3-4B-Instruct · LoRA · ONNX Runtime Web · WebGPU · Optimum · RAGAS_

[app](https://ankorn.github.io/redred/) · [code](https://github.com/ankorn/redred)

- Improved summarization quality, achieving a gain of **ROUGE-Lsum +10.3%** (ROUGE-Lsum = 0.29 → ROUGE-Lsum = 0.32), **ROUGE-1 +24.3%** (ROUGE-1 = 0.37 → ROUGE-1 = 0.46). To achieve this, I fine-tuned the multimodal LLM gemma-4-E2B-it on the mRedditSum dataset using LoRA and Unsloth
- Set up browser inference with ONNX Runtime Web and streaming generation; the 4-bit quantized model weighs 3.5 GB and runs using WebGPU
- Built an evaluation pipeline on RAGAS with Qwen3-4B-Instruct as LLM-as-judge; used it to compare the SummarizationScore of the base and fine-tuned models
- Implemented scraping of Reddit threads and images using Yandex Cloud Functions

---

## Assessment and Onboarding

- Passed the ML/NLP assessment at T-Bank in the following sections: algorithms — senior-; classical ML — junior+; NLP — junior+. Grade based on the section results — junior+
- Completed onboarding in the T-Bank telephony team: learned LangFuse for tracing LLM applications and prompt engineering according to the RTCF Framework

---

## Skills

**ML / NLP**
Agentic RAG · Text classification · language modeling · seq2seq · attention · transformers · transfer learning · LLM · PEFT/LoRA · quantization · retrieval

**Model Training**
Dense retrieval, contrastive learning (MultipleNegativesRankingLoss, GISTEmbedLoss), hard negative mining · fine-tuning multimodal LLMs · synthetic data generation via LLM

**Metrics**
recall@k · NDCG@k · ROUGE (ROUGE-Lsum, ROUGE-1) · paired bootstrap · confidence intervals · RAGAS (SummarizationScore)

**Inference / MLOps**
Docker · ONNX / Optimum, quantization (q4/q8), browser inference (ONNX Runtime Web) · vector search (pgvector, KNN) · deployment on HF Spaces, Supabase Edge Functions, Yandex Cloud Functions

**Stack**
Python, PyTorch, HF Transformers/Datasets/PEFT, Unsloth, sentence-transformers · LangChain · LangFuse

**Learning**
NLP course at SHAD ([fork with solutions](https://github.com/ankorn/nlp_course)) — trained models on all topics · NLP Course For You

---

## Work Experience

### T-Bank — Frontend Engineer · 2023–2026

- Set up monitoring of process and product metrics (using Grafana), availability indicators, and alerting for microfrontends
- Independently brought three products to production in the microfrontend architecture of the personal account
- Led the algorithms section of technical interviews for a year; mentored an intern to a junior position

---

## Additional

- **English:** C1