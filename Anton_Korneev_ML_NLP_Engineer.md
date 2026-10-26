---
---

---

# Антон Корнеев

**ML / NLP Engineer** (ex-Frontend) · PyTorch · HF Transformers · Agentic RAG · LoRA

+7 993 465 45 10 · tg: @ankornlog · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

Инженер с 9-летним опытом коммерческой разработки, специализируюсь на LLM-приложениях. Строю системы от подготовки данных и обучения моделей до деплоя. Фокус — agentic RAG: retrieval, tool calling, streaming, memory, MCP. Реализовал два проекта: cross-community поиск с обученными retriever и reranker и LLM-агентом поверх них, а также обученный мультимодальный саммарайзер с инференсом в браузере. Ищу позицию ML/NLP Engineer с уклоном в LLM-агентов.

---

## Проекты

### arcanumchat — agentic RAG над cross-community корпусом по вселенной Arcanum

_LangChain · MCP · PyTorch · sentence-transformers · BAAI/bge-m3 · BAAI/bge-reranker-v2-m3 · Qwen 3.6 35B · pgvector/Supabase · HF Spaces · vLLM · FastAPI · Docker_

[приложение](https://ankorn.github.io/arcanumchat/) · [код](https://github.com/ankorn/arcanumsearch)

- Соскрапил документы из разнородных источников(arcanum wiki, Reddit треды, описание патчей и модов), убрал документы-аггрегаторы, определил чанкинг документов, нормализовал треды
- Построил инференс на vLLM и сгенерировал синтетические запросы той же моделью, что и в агенте на проде - Qwen3.6-35B-A3B, выполнил на NVIDIA A100 80GB
- В ручную разметил [датасет](https://huggingface.co/datasets/pameydorke/arcanumchat-cross-platform-with-vague-queries-qwen-36-a3b-fp8) для оценки, реализовал алгоритм оценки с помощью попарного бутстрапа и доверительных интервалов
- Обучил bi-encoder [bge-m3]() и cross-encoder [bge-reranker-v2-m3]() на hard-negative датасетах, получил статзначимый приорист: **recall@10 0.89 -> 0.95** (95% ДИ [0.0211, 0.1000]); **ndcg@10: 0.79 -> 0.87** (95% ДИ [0.0484, 0.1175])
- Задеплоил retriever и reranker в HF Spaces
- Поместил ембеддинги в Supabase с помощью pgvector, добавил sql функцию knn и edge функцию для поиска и реранжирования релевантных документов
- Написал серверную логику агента с помощью LangChain и FastAPI, для streaming использовал WebSocket
- Инструменты агента: retrieval пайплайн и инструмент для математики на MCP-сервере
- Задеплоил сервер с помощью Docker

### redred — мультимодальный саммарайзер постов Reddit, работающий в браузере

_PyTorch · HF Transformers · Unsloth · Gemma 4 (multimodal) · LoRA · ONNX Runtime Web · Optimum · RAGAS_

[приложение](https://ankorn.github.io/redred/) · [код](https://github.com/ankorn/redred)

- Дообучил мультимодальную LLM gemma-4-E2B-it, квантизованную в 4 бита, на mRedditSum с помощью LoRA и Unsloth — **rougeLsum 0.29 → 0.32, rouge1 0.37 → 0.46**
- Построил пайплайн оценки на RAGAS с Qwen3-4B-Instruct в качестве LLM-as-judge
- Настроил браузерный инференс ONNX Runtime Web со streaming-генерацией
- Скрапинг Reddit тредов и изображений реализовал с помощью Yandex Cloud Functions

---

## Навыки

**ML / NLP**
Agentic RAG · Text classification · language modeling · seq2seq · attention · transformers · transfer learning · LLM · PEFT/LoRA · RLHF · квантизация · retrieval

**Обучение моделей**
Dense retrieval, contrastive learning(MultipleNegativesRankingLoss, GISTEmbedLoss), hard negative mining · файнтюнинг мультимодальных LLM · систематический HPO · диагностика переобучения · генерация синтетических данных через LLM

**Метрики**
recall@k · ndcg@k · ROUGE(rouge1, rougeLsum) · попарный бустрап, доверительные интервалы · RAGAS(SummaryScore, SemanticSimilarity)

**Инференс / MLOps**
Docker · ONNX / Optimum, квантизация (q4/q8), браузерный inference (ONNX Runtime Web) · vector search (pgvector, KNN) · деплой на HF Spaces, Supabase Edge Functions, Yandex Cloud Functions

**Стек**
Python, PyTorch, HF Transformers/Datasets/PEFT, Unsloth, sentence-transformers · LangChain

**Обучение**
NLP-курс ШАД ([форк с решениями](https://github.com/ankorn/nlp_course)) — обучал модели по всем темам · NLP Course For You · ML Crash Course · Deep Learning Specialization (Andrew Ng)

---

## Опыт работы

### Т-Банк — Frontend Engineer · 2023–2026

- Настроил мониторинг процессных и продуктовых метрик(с помощью Grafana), индикаторы доступности и алертинг для микрофронтов _(навык, применимый к ML-observability)_
- Самостоятельно вывел в прод три продукта в микрофронтовой архитектуре личного кабинета
- Год вёл алгоритмическую секцию технических интервью; менторил стажёра до junior-позиции

### Fibbee — Frontend Engineer (стартап) · 2021–2023

- Единственный фронтенд-разработчик: построил продукт с нуля (React, TypeScript, Redux Toolkit)

### Altarix — Frontend Engineer · 2017–2021

- Московская электронная школа: оптимизировал стартовую загрузку страниц на 20%
- ДОМ.РФ: упростил стек, сократив время разработки логики на 30% (React Query)
- Вёл внутренний курс по JS, менторил junior-разработчиков

---

## Дополнительно

- **Английский:** C1

---
