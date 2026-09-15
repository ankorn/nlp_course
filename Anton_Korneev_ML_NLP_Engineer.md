
---

# Антон Корнеев

**ML / NLP Engineer** (ex-Frontend) · PyTorch · HF Transformers · RAG · LoRA

+7 993 465 45 10 · tg: @ankornlog · [GitHub](https://github.com/ankorn) · [HuggingFace](https://huggingface.co/pameydorke)

---

## Summary

Инженер с 9-летним опытом продакшн-разработки, специализируюсь на NLP. Строю end-to-end ML-решения: от подготовки данных и обучения моделей до деплоя в прод. Построил два самостоятельных проекта, покрывающих ключевые NLP-задачи — retrieval с contrastive learning и файнтюнинг мультимодальной LLM для суммаризации с inference полностью в браузере. Ищу позицию ML/NLP Engineer.

---

## Проекты

### arcanumsearch — cross-community семантический поиск по вселенной игры Arcanum
*PyTorch · sentence-transformers · BAAI/bge-m3 · Qwen 7B/14B · pgvector/Supabase · HF Spaces · Yandex Cloud Functions · TS/React*

[demo](https://ankorn.github.io/arcanumsearch/) · [code](https://github.com/ankorn/arcanumsearch) · [tasks](https://github.com/ankorn/arcanumsearch/blob/main/TASKS.md)

- Обучил dense retriever на `BAAI/bge-m3`; сравнил `MultipleNegativesRankingLoss` и `GISTEmbedLoss`, выбрал оптимум по трейд-оффу recall@k / память / скорость
- Построил пайплайн генерации синтетических обучающих запросов через Qwen; prompt-engineering'ом устранил утечку скрытой информации, а переход на модель побольше (7B → 14B) убрал слишком невнятные запросы — **recall@5 вырос с 0.90 до 0.96**
- Реализовал майнинг hard negatives; диагностировал и смягчил catastrophic forgetting
- Развернул инференс в проде: эмбеддинги в PostgreSQL + pgvector (Supabase), KNN-поиск через SQL-функцию, feature extraction на HF Spaces (Zero GPU)
- Спроектировал data-пайплайн: скрапинг через Yandex Cloud Functions с обходом rate-limit, чанкинг по секциям, дедупликация, фильтрация stub/aggregator-страниц, нормализация Reddit-тредов
- По результатам продуктового анализа переориентировал продукт на уникальную ценность — cross-community поиск (патчи, моды, баги из Reddit / Nexus Mods), недоступный в нативном поиске Fandom

### redred — мультимодальный саммарайзер постов Reddit, работающий в браузере
*PyTorch · HF Transformers · Unsloth · Gemma 4 (multimodal) · LoRA · ONNX Runtime Web · Optimum · Yandex Cloud Functions · TS/React*

[demo](https://ankorn.github.io/redred/) · [code](https://github.com/ankorn/redred) · [tasks](https://github.com/ankorn/redred/blob/main/TASKS.md)

- Дообучил мультимодальную LLM (Gemma 4, image + text) на mRedditSum через LoRA/Unsloth — **rougeLsum 0.29 → 0.32, rouge1 0.37 → 0.46**
- Провёл систематический тюнинг гиперпараметров (learning rate, LoRA rank, dropout, weight decay, scheduler, label smoothing); диагностировал переобучение при высоком LoRA rank
- Принял продуктовое решение о смене подхода: TL;DR-датасет давал слишком короткие ироничные саммари → перешёл на мультимодальный mRedditSum, т.к. на Reddit изображение несёт ключевой смысл
- Решил инженерные проблемы обучения: OOM при eval (`preprocess_logits_for_metrics`, кастомный `prediction_step`), ROUGE-based checkpoint selection и early stopping
- Настроил браузерный inference: ONNX Runtime Web со streaming-генерацией, форматирование мультимодального ввода идентично обучению
- Осознанно выбрал браузерный inference (vs Ollama / сервер / widget): приватность данных, нулевые GPU-затраты; для скрапинга Reddit-тредов, изображений и обхода CORS реализовал Yandex Cloud Functions
- Столкнулся с отсутствием поддержки Gemma 4 в библиотеке ONNX; кастомные экспорты оказались нестабильными, поэтому принял решение использовать базовую модель в проде до обновления ONNX



---

## Навыки

**ML / NLP**
Text classification · language modeling · seq2seq · attention · transformers · transfer learning · LLM · PEFT/LoRA · RLHF · квантизация · retrieval · agents

**Обучение моделей**
Dense retrieval, contrastive learning(MultipleNegativesRankingLoss, GISTEmbedLoss), hard negative mining · файнтюнинг мультимодальных LLM · систематический HPO · диагностика переобучения и catastrophic forgetting · генерация синтетических данных через LLM

**Метрики**
recall@k · ROUGE(rouge1, rougeLsum)

**Инференс / MLOps**
ONNX / Optimum, квантизация (q4/q8), браузерный inference (ONNX Runtime Web) · vector search (pgvector, KNN) · деплой на HF Spaces (Zero GPU), Supabase Edge Functions, Yandex Cloud Functions

**Стек**
Python, PyTorch, HF Transformers/Datasets/PEFT, Unsloth, sentence-transformers · TypeScript, React

**Обучение (подтверждение теории)**
NLP-курс ШАД ([форк с решениями](https://github.com/ankorn/nlp_course)) — обучал модели по всем темам · NLP Course For You · ML Crash Course · Deep Learning Specialization (Andrew Ng)

---

## Опыт работы

### Т-Банк — Frontend Engineer · 2023–2026
- Настроил мониторинг процессных и продуктовых метрик, индикаторы доступности и алертинг для микрофронтов *(навык, применимый к ML-observability)*
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