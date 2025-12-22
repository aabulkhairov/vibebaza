---
title: Feyod MCP сервер
description: MCP сервер, который предоставляет интерфейс на естественном языке для запросов к данным футбольных матчей Feyenoord, преобразуя вопросы в SQL запросы и возвращая информацию о матчах, статистику игроков и данные о соперниках.
tags:
- Database
- AI
- Analytics
- Search
- API
author: Community
featured: false
---

MCP сервер, который предоставляет интерфейс на естественном языке для запросов к данным футбольных матчей Feyenoord, преобразуя вопросы в SQL запросы и возвращая информацию о матчах, статистику игроков и данные о соперниках.

## Установка

### Docker Hub

```bash
docker pull jeroenvdmeer/feyod-mcp
```

### Из исходников

```bash
git clone https://github.com/jeroenvdmeer/feyod-mcp.git
git clone https://github.com/jeroenvdmeer/feyod.git
cd feyod-mcp
uv venv
.venv\Scripts\activate  # Windows
# or
source .venv/bin/activate  # macOS/Linux
uv add "mcp[cli]" langchain langchain-openai langchain-google-genai python-dotenv aiosqlite
```

### Настройка базы данных

```bash
cd ../feyod
sqlite3 feyod.db < feyod.sql
```

### Запуск Docker

```bash
docker run -p 8000:8000 \
  -e LLM_PROVIDER="your_llm_provider" \
  -e LLM_API_KEY="your_api_key" \
  jeroenvdmeer/feyod-mcp
```

### Режим разработки

```bash
mcp dev main.py
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `answer_feyenoord_question` | Отвечает на вопросы о Feyenoord. Вопросы можно задавать на естественном языке, в текстовом виде, и они могут быть... |

## Возможности

- Интерфейс на естественном языке для запросов к данным футбольных матчей Feyenoord
- Преобразует вопросы на естественном языке в SQL запросы с использованием LangChain
- Валидирует и пытается исправить неверные SQL запросы с помощью LLM
- Поддерживает множество провайдеров LLM (OpenAI, Google и др.) через фабрику провайдеров
- Few-shot примеры для лучшей точности генерации SQL
- Публичная HTTP конечная точка доступна по адресу https://mcp.feyod.nl/mcp
- Поддержка Docker контейнеров с готовыми образами
- SQLite база данных с полными данными матчей Feyenoord

## Переменные окружения

### Обязательные
- `DATABASE_PATH` - Путь к файлу SQLite базы данных (относительно папки mcp или абсолютный)
- `LLM_PROVIDER` - Провайдер LLM для использования (например, 'google', 'openai')
- `LLM_API_KEY` - API ключ для провайдера LLM

### Опциональные
- `HOST` - Привязка хоста сервера (по умолчанию localhost/127.0.0.1)
- `LOG_LEVEL` - Уровень логирования (например, DEBUG, INFO, WARNING, ERROR)
- `LLM_MODEL` - Конкретная модель для использования (например, 'gemini-2.5-flash')
- `EXAMPLE_SOURCE` - Источник примеров ('local' или 'mongodb')
- `EXAMPLE_DB_CONNECTION_STRING` - Строка подключения MongoDB при использовании MongoDB для примеров
- `EXAMPLE_DB_NAME` - Имя базы данных MongoDB для примеров
- `EXAMPLE_DB_COLLECTION` - Имя коллекции MongoDB для примеров

## Ресурсы

- [GitHub Repository](https://github.com/jeroenvdmeer/feyod-mcp)

## Примечания

Требует Python 3.10+. Базовая база данных Feyod поддерживается в отдельном репозитории (jeroenvdmeer/feyod). Публично доступная конечная точка по адресу https://mcp.feyod.nl/mcp. Реализует контроль безопасности, включая валидацию SQL запросов и доступ к базе данных только для чтения. Поддерживает отладку с помощью MCP Inspector.