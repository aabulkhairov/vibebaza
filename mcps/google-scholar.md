---
title: Google-Scholar MCP сервер
description: MCP сервер, который предоставляет возможности поиска в Google Scholar для нахождения академических статей и исследований через HTTP транспорт.
tags:
- Search
- AI
- API
- Analytics
- Integration
author: Community
featured: false
---

MCP сервер, который предоставляет возможности поиска в Google Scholar для нахождения академических статей и исследований через HTTP транспорт.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @mochow13/google-scholar-mcp --client claude
```

### Из исходного кода

```bash
git clone <repository-url>
cd google-scholar-mcp
cd server
npm install
npm run build
cd client
npm install
npm run build
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_google_scholar` | Поиск в Google Scholar академических статей и исследований с настраиваемыми параметрами поиска и ре... |

## Возможности

- Поиск академических статей в Google Scholar
- Потоковый HTTP транспорт с Server-Sent Events
- Поддержка множественных сессий для одновременных подключений
- Интеграция с AI моделью Google Gemini
- Постоянный контекст и история диалогов
- Уведомления в реальном времени через SSE потоки
- Расширяемый фреймворк регистрации инструментов
- Комплексная обработка ошибок и логирование

## Переменные окружения

### Обязательные
- `GEMINI_API_KEY` - Необходим для интеграции клиентского AI с Google Gemini

### Опциональные
- `PORT` - Конфигурация порта сервера

## Примеры использования

```
Find recent papers about machine learning in healthcare
```

```
What about specifically for diagnostic imaging?
```

## Ресурсы

- [GitHub Repository](https://github.com/mochow13/google-scholar-mcp)

## Примечания

Сервер работает на порту 3000 с эндпоинтами POST /mcp для коммуникации и GET /mcp для SSE потоков. Включает в себя как серверную, так и клиентскую реализацию, причем клиент предоставляет интерактивный интерфейс чат-цикла.