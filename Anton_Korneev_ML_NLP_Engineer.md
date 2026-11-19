---
---

---

# Антон Корнеев

**ML / NLP Engineer** (ex-Frontend) · PyTorch · HF Transformers · Agentic RAG

+7 993 465 45 10 · telegram: @ankornlog · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

Инженер с 9-летним опытом коммерческой разработки. Год назад прошёл аттестацию ML/NLP в Т-Банке с результатом **junior+** и онбординг в команде телефонии, а затем реализовал два своих проекта: cross-community поиск с обученными retriever и reranker и LLM-агентом поверх них, а также обученный мультимодальный саммарайзер с инференсом в браузере. Строю LLM-приложения от подготовки данных и обучения моделей до деплоя. Ищу позицию ML/NLP Engineer.

---

## Проекты

### arcanumchat — agentic RAG над cross-community корпусом по вселенной Arcanum

_PyTorch · sentence-transformers · LangChain · MCP · bge-m3 · bge-reranker-v2-m3 · Qwen3.6-35B-A3B · pgvector/Supabase · HF Spaces · vLLM · FastAPI · Docker_

[приложение](https://ankorn.github.io/arcanumchat/) · [код](https://github.com/ankorn/arcanumsearch)

- Улучшил качество RAG на выборке из 20 кандидатов: получил [статистически значимый прирост](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_eval.ipynb) **recall@10 0.90 -> 0.96** и **ndcg@10: 0.79 -> 0.87** (95% ДИ прироста [0.0260, 0.0990] и [0.0406, 0.1170] соответственно). Для этого обучил bi-encoder [bge-m3](https://huggingface.co/pameydorke/arcanumchat-retriever-bge-m3-v2) и cross-encoder [bge-reranker-v2-m3](https://huggingface.co/pameydorke/arcanumchat-reranker-bge-reranker-v2-m3-v2) на hard-negative датасетах; значимость оценил с помощью парного бутстрапа по запросам и доверительных интервалов
- Улучшил качество RAG на выборке из 10 кандидатов, получив небольшой, но [статистически значимый прирост](https://github.com/ankorn/arcanumsearch/blob/main/retrieval_hybrid_search_eval.ipynb) **recall@5 0.90 -> 0.92** (95% ДИ [0.0052, 0.0417]): реализовал гибридный поиск dense + BM25 и RRF
- Сгенерировал [датасет](https://huggingface.co/datasets/pameydorke/arcanumchat-cross-platform-with-vague-queries-qwen-36-a3b-fp8) синтетических запросов для RAG: запустил Qwen3.6-35B-A3B-FP8 с помощью vLLM на NVIDIA A100 80GB, построил пайплайн генерации, написал и протестировал промпты; датасет использован для обучения retrieval-моделей
- Реализовал скрапинг более 1000 документов из разнородных источников (arcanum wiki, Reddit треды, описание патчей и модов), убрал документы-агрегаторы, применил структурный чанкинг документов по секциям википедии, нормализовал треды
- Задеплоил retriever и reranker в HF Spaces; поместил ембеддинги в Supabase с помощью pgvector, добавил SQL функцию KNN
- Написал серверную логику агента с помощью LangChain и FastAPI; streaming по WebSocket, memory с помощью thread_id; задеплоил сервер с помощью Docker
- В основе агента облачный Qwen3.6-35B-A3B через OpenAI-совместимый API; инструменты агента — retrieval пайплайн и инструмент для математики на MCP-сервере

<br/>

### redred — мультимодальный саммарайзер постов Reddit, работающий в браузере

_PyTorch · HF Transformers · Unsloth · gemma-4-E2B-it (multimodal) · Qwen3-4B-Instruct · LoRA · ONNX Runtime Web · WebGPU · Optimum · RAGAS_

[приложение](https://ankorn.github.io/redred/) · [код](https://github.com/ankorn/redred)

- Улучшил качество суммаризации, получив прирост **ROUGE-Lsum 0.29 → 0.32, ROUGE-1 0.37 → 0.46**. Для этого обучил мультимодальную LLM gemma-4-E2B-it, на mRedditSum с помощью LoRA и Unsloth 
- Настроил браузерный инференс ONNX Runtime Web со streaming-генерацией; модель, квантизованная в 4 бита, весит 3.5GB и выполняется с помощью WebGPU
- Построил пайплайн оценки на RAGAS с Qwen3-4B-Instruct в качестве LLM-as-judge; использовал для сравнения SummarizationScore базовой и обученной моделей
- Реализовал скрапинг Reddit тредов и изображений с помощью Yandex Cloud Functions

---

## Аттестация и онбординг

- Прошёл аттестацию ML/NLP в Т-Банке по секциям: алгоритмы — senior-; классическое ML — junior+: NLP — junior+. Грейд по результатам секций — junior+
- Прошёл онбординг в команде телефонии Т-Банка: освоил LangFuse для трейсинга LLM-приложений и промпт-инжиниринг по RTCF Framework

---

## Навыки

**ML / NLP**
Agentic RAG · Text classification · language modeling · seq2seq · attention · transformers · transfer learning · LLM · PEFT/LoRA · квантизация · retrieval

**Обучение моделей**
Dense retrieval, contrastive learning (MultipleNegativesRankingLoss, GISTEmbedLoss), hard negative mining · файнтюнинг мультимодальных LLM · генерация синтетических данных через LLM

**Метрики**
recall@k · ndcg@k · ROUGE (ROUGE-Lsum, ROUGE-1) · парный бустрап · доверительные интервалы · RAGAS (SummarizationScore)

**Инференс / MLOps**
Docker · ONNX / Optimum, квантизация (q4/q8), браузерный inference (ONNX Runtime Web) · vector search (pgvector, KNN) · деплой на HF Spaces, Supabase Edge Functions, Yandex Cloud Functions

**Стек**
Python, PyTorch, HF Transformers/Datasets/PEFT, Unsloth, sentence-transformers · LangChain · LangFuse

**Обучение**
NLP-курс ШАД ([форк с решениями](https://github.com/ankorn/nlp_course)) — обучал модели по всем темам · NLP Course For You

---

## Опыт работы

### Т-Банк — Frontend Engineer · 2023–2026

- Настроил мониторинг процессных и продуктовых метрик (с помощью Grafana), индикаторы доступности и алертинг для микрофронтов
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
