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

Здравствуйте!

Меня заинтересовала вакансия в «Потоке»: суммаризация встреч и агентные подсказки — именно тот класс задач, на которых я специализируюсь. У меня 9 лет в продакшн-разработке, последние годы я сфокусирован на NLP и LLM-приложениях, а два самостоятельных end-to-end проекта дали мне прямой опыт по всем ключевым требованиям вакансии.

Резюме встреч — я это уже делал. В проекте redred я дообучил мультимодальную LLM (LoRA/Unsloth) для суммаризации контента Reddit и построил пайплайн оценки качества на RAGAS с LLM-as-judge.

Агенты и RAG: в arcanumchat я построил agentic RAG: LLM вызывает semantic search как tool, стриминг по WebSocket, многоходовый диалог, MCP-интеграции. Отдельно обучил dense retriever (bge-m3) с майнингом hard negatives и генерацией синтетических запросов — recall@5 вырос с 0.90 до 0.96. Это же ядро нужно и для «договорённостей и следующих шагов» из встреч.

Прод: вывожу продукты из прототипов в эксплуатацию сам. FastAPI + Docker, pgvector, облачные функции, Hugging Face Spaces, браузерный inference. Привык отвечать за фичу целиком — от гипотезы и данных до метрик пользы для пользователя, именно так переориентировал arcanumchat на уникальную ценность после продуктового анализа.

Стек вакансии (LangChain, RAG, fine-tuning/LoRA, FastAPI) — мой инструментарий.

Буду рад обсудить, как мой опыт адаптировать под масштаб банка.

С уважением,
Антон Корнеев.

---

Добрый день!

Меня заинтересовала вакансия: у меня ровно тот профиль, который вы описываете — инженер с 9-летним опытом продакшн-разработки, последние годы полностью сфокусирован на NLP и LLM-приложениях.

Из релевантного опыта: agentic RAG в проде. Самостоятельно спроектировал и задеплоил систему, где LLM-агент на LangChain вызывает semantic search как tool, диалог идёт через memory со стримингом по WebSocket. Это не PoC — работающий сервис: FastAPI + Docker, pgvector/Supabase, HF Spaces.

Метрики и итеративное улучшение: занимаюсь этим системно: обучил dense retriever (bge-m3), майнил hard negatives на FAISS, выбрал loss по трейд-оффу recall/память/скорость. Практический результат — recall@5: 0.90 → 0.96. Во втором проекте построил оценку на RAGAS с LLM-as-judge и семантической близостью, что выявило расхождение с ROUGE и дало точки роста.

MCP: Реализовал MCP-сервер с tool-ами для агента

Полный цикл от данных до продакшена: от синтетической генерации датасетов на Qwen до инференса в браузере через ONNX Runtime Web — опыт есть на всех этапах, от подготовки данных и обучения моделей до деплоя в прод
Пишу на Python, пишу также на TypeScript/React (все фронтенды моих проектов — свои). Знаком с FAISS и pgvector. C# — не основной стек, но готов освоить под ваши задачи.

Буду рад рассказать подробнее на встрече — можно прямо по живому демо одного из проектов.

Резюме отдельным файлом прилагаю.

С уважением,
Антон Корнеев.

---

Здравствуйте!

Меня заинтересовала вакансия в AI Disrupt and CoreTeam — я именно там, где хочу развиваться: на стыке исследований и продакшна.

Я инженер с 9-летним опытом продакшн-разработки. Последние годы целиком сфокусирован на ml/nlp-приложениях и построил два end-to-end продукта в одиночку — от данных до деплоя:

- Agentic RAG поверх cross-community корпуса: LLM вызывает semantic search как tool, многоходовый диалог, streaming по WebSocket. Обучил dense retriever (bge-m3), поднял recall@5 с 0.90 до 0.96 за счёт генерации синтетических запросов и майнинга hard negatives. Прод-контур на FastAPI + Docker + PostgreSQL + pgvector.
- Мультимодальный саммарайзер (файнтюн Gemma через LoRA/Unsloth, rougeLsum 0.29 → 0.32) с браузерным inference на ONNX Runtime Web — инференс без сервера и GPU-затрат.

Прямое попадание в ваши требования:

- Eval и качество: построил пайплайн оценки на RAGAS с LLM-as-a-judge (Qwen3) + семантическая близость на эмбеддингах — измеряю качество сверх n-граммных метрик и умею находить расхождения между ними.
- BERT-like и дообучение: сравнивал лосс-функции (MultipleNegativesRankingLoss vs GISTEmbedLoss) по трейд-оффу recall/память/скорость, системно тюнил гиперпараметры (LR, LoRA rank, dropout).
- PyTorch, NumPy, pandas, ООП — база моей инженерной практики.
- ONNX-инференс — реализовал в проде и столкнулся с его реальными ограничениями (кастомный экспорт нестабилен, соблюдение идентичности форматирования ввода при обучении и inference).
- Самостоятельность от идеи до результата: оба проекта я спроектировал, обосновал продуктовые решения (включая осознанную смену подхода по данным и переориентирование на уникальную ценность) и вывел в прод.

Хочу применить этот опыт на задачах, которые каждый день решают реальные бизнес-проблемы обслуживания клиентов — и уверен, что умею быстро проверять гипотезы и доводить их до работающего продукта.
Буду рад обсудить на интервью, как мой опыт может ускорить развитие ваших агентов.

Резюме: https://drive.google.com/file/d/11_puLSFADPwhD1yp0K080i1YwRG-c-xJ/view?usp=sharing

С уважением,
[Имя]
