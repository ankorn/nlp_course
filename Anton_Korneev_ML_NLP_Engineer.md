---
---

---

# Антон Корнеев

**ML / NLP Engineer** (ex-Frontend) · PyTorch · HF Transformers · Agentic RAG · LoRA

+7 993 465 45 10 · tg: @ankornlog · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

Инженер с 9-летним опытом коммерческой разработки, специализируюсь на LLM-приложениях. Строю end-to-end системы: от подготовки данных и обучения моделей до деплоя. Фокус — agentic RAG: retrieval, tool calling, streaming, memory, MCP. Реализовал два проекта: cross-community поиск с обученными retriever и reranker и LLM-агентом поверх них, а также обученный мультимодальный саммарайзер с inference в браузере. Ищу позицию ML/NLP Engineer с уклоном в LLM-агентов.

---

## Проекты

### arcanumchat — agentic RAG над cross-community корпусом по вселенной Arcanum

_LangChain · MCP · PyTorch · sentence-transformers · BAAI/bge-m3 · BAAI/bge-reranker-v2-m3 · Qwen 3.6 35B · pgvector/Supabase · HF Spaces · vLLM · FastAPI · Docker_

[приложение](https://ankorn.github.io/arcanumchat/) · [код](https://github.com/ankorn/arcanumsearch)

- соскрапил из нескольких источников, чанкинг, уникальная ценность (ссылка на дс)
- построил инференс на vLLM и ситезировал запросы той же моделью, что и в агенте на проде - Qwen 3.6 35B 
- в ручную разметил датасет для оценки, реализовал код оценки с помощью попарного бутстрапа и доверительных интервалов
- обучил bi-encoder bge-m3 и cross-encoder bge-reranker-v2-m3 на hard-negative датасетах, получил статзначимый приорист по сравнению с базовыми моделями: recall@10 0.89 -> 0.95 (95% CI [0.0211, 0.1000]); ndcg@10: 0.79 -> 0.87 (95% CI [0.0484, 0.1175])
- задеплоил модели в HF Spaces
- поместил ембеддинги в Supabase с помощью pgvector, добавил sql функцию knn и edge функцию для поиска и реранжирования релевантных документов
- написал серверную логику агента с помощью LangChain, FastAPI, для streaming использовал WebSocket
- в качестве LLM для агента использовал Qwen3.6-35B-A3B
- реализовал MCP-сервер с tool для математики
- задеплоил сервер с помощью Docker

### redred — мультимодальный саммарайзер постов Reddit, работающий в браузере

_PyTorch · HF Transformers · Unsloth · Gemma 4 (multimodal) · LoRA · ONNX Runtime Web · Optimum_

[приложение](https://ankorn.github.io/redred/) · [код](https://github.com/ankorn/redred)

- Дообучил мультимодальную LLM (Gemma 4, image + text) на mRedditSum через LoRA/Unsloth — **rougeLsum 0.29 → 0.32, rouge1 0.37 → 0.46**
- Построил пайплайн оценки качества на RAGAS с LLM-as-judge (Qwen3-4B-Instruct) и семантической близостью на эмбеддингах (Qwen3-Embedding-8B), позволяющий измерять качество сверх n-граммных метрик. Выявил расхождение между ROUGE и семантическими метриками; ограниченный размер eval-выборки задокументирован как направление для дальнейшей работы
- Провёл систематический тюнинг гиперпараметров (learning rate, LoRA rank, dropout, weight decay, scheduler, label smoothing); диагностировал переобучение при высоком LoRA rank
- Принял продуктовое решение о смене подхода: TL;DR-датасет давал слишком короткие ироничные саммари → перешёл на мультимодальный mRedditSum, т.к. на Reddit изображение несёт ключевой смысл
- Решил инженерные проблемы обучения: OOM при eval (`preprocess_logits_for_metrics`, кастомный `prediction_step`), ROUGE-based checkpoint selection и early stopping
- Настроил браузерный inference: ONNX Runtime Web со streaming-генерацией, форматирование мультимодального ввода идентично обучению
- Осознанно выбрал браузерный inference (vs Ollama / сервер / widget): приватность данных, нулевые GPU-затраты; для скрапинга Reddit-тредов, изображений и обхода CORS реализовал Yandex Cloud Functions
- Столкнулся с отсутствием поддержки Gemma 4 в библиотеке ONNX; кастомные экспорты оказались нестабильными, поэтому принял решение использовать базовую модель в проде до обновления ONNX

---

## Навыки

**ML / NLP**
Agentic RAG · Text classification · language modeling · seq2seq · attention · transformers · transfer learning · LLM · PEFT/LoRA · RLHF · квантизация · retrieval

**Обучение моделей**
Dense retrieval, contrastive learning(MultipleNegativesRankingLoss, GISTEmbedLoss), hard negative mining · файнтюнинг мультимодальных LLM · систематический HPO · диагностика переобучения · генерация синтетических данных через LLM

**Метрики**
recall@k · ndcg@k · ROUGE(rouge1, rougeLsum) · RAGAS(SummaryScore, SemanticSimilarity)

**Инференс / MLOps**
Docker · ONNX / Optimum, квантизация (q4/q8), браузерный inference (ONNX Runtime Web) · vector search (pgvector, KNN) · деплой на HF Spaces, Supabase Edge Functions, Yandex Cloud Functions

**Стек**
Python, PyTorch, HF Transformers/Datasets/PEFT, Unsloth, sentence-transformers · LangChain · TypeScript, React

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
