---
---

---

# Антон Корнеев

**ML / NLP Engineer** (ex-Frontend) · PyTorch · HF Transformers · Agentic RAG · LoRA

+7 993 465 45 10 · tg: @ankornlog · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

Инженер с 9-летним опытом продакшн-разработки, специализируюсь на NLP и LLM-приложениях. Строю end-to-end системы: от подготовки данных и обучения моделей до деплоя в прод. Фокус — agentic RAG: retrieval, tool calling, streaming, MCP-интеграции. Реализовал два самостоятельных проекта: cross-community поиск с обученным dense retriever и LLM-агентом поверх него, а также файнтюнинг мультимодальной LLM для суммаризации с inference полностью в браузере. Ищу позицию ML/NLP Engineer с уклоном в LLM-агентов.

---

## Проекты

### arcanumchat — agentic RAG над cross-community корпусом по вселенной Arcanum

_LangChain(custom tools, streaming, memory) · MCP · FastAPI · Docker · PyTorch · sentence-transformers · BAAI/bge-m3 · Qwen 7B/14B · pgvector/Supabase · HF Spaces · Yandex Cloud Functions · TS/React_

[приложение](https://ankorn.github.io/arcanumchat/) · [код](https://github.com/ankorn?tab=repositories&q=arcanum&type=&language=&sort=) · [задачи](https://github.com/ankorn/arcanumsearch/blob/main/TASKS.md)

- Написал и задеплоил agentic RAG: LLM вызывает semantic search как tool, ответ стримится токен за токеном по WebSocket, многоходовый диалог реализован с помощью LangChain memory
- Реализовал MCP-сервер с tool для математики, чтобы агент мог делать вычисления по игровым механикам
- Развернул прод-контур: FastAPI + Docker для агента, pgvector/Supabase для эмбеддингов, HF Spaces для feature extraction по дообученной модели, Yandex Cloud Functions для скрапинга
- Обучил dense retriever на `BAAI/bge-m3`; сравнил `MultipleNegativesRankingLoss` и `GISTEmbedLoss`, выбрал оптимум по трейд-оффу recall@k / память / скорость
- Построил пайплайн генерации синтетических запросов на Qwen: устранил утечку скрытой информации через промпт-инжиниринг, заменил генератор на Qwen-14B — recall@5: 0.90 → 0.96, ndcg@10: 0.70 → 0.73
- Реализовал майнинг hard negatives на FAISS, что устранило застой метрик (recall@k / ndcg) при дообучении на базовом датасете
- По результатам продуктового анализа переориентировал продукт на уникальную ценность — cross-community поиск (патчи, моды, баги из Reddit / Nexus Mods), недоступный в нативном поиске Fandom

### redred — мультимодальный саммарайзер постов Reddit, работающий в браузере

_PyTorch · HF Transformers · Unsloth · Gemma 4 (multimodal) · LoRA · ONNX Runtime Web · Optimum · Yandex Cloud Functions · TS/React_

[приложение](https://ankorn.github.io/redred/) · [код](https://github.com/ankorn/redred) · [задачи](https://github.com/ankorn/redred/blob/main/TASKS.md)

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
