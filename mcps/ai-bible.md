---
title: ai-Bible MCP сервер
description: MCP сервер для надёжного и воспроизводимого поиска библейских стихов и текстов
  для AI/LLM интерпретации, исследований и образовательных целей с воспроизводимыми
  результатами.
tags:
- Database
- Search
- AI
- API
- Integration
author: AdbC99
featured: false
---

MCP сервер для надёжного и воспроизводимого поиска библейских стихов и текстов для AI/LLM интерпретации, исследований и образовательных целей с воспроизводимыми результатами.

## Установка

### Docker

```bash
docker build -f completions/Dockerfile -t mcp-server .
docker run -p 8002:8000 mcp-server
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get-verse` | Получить библейские стихи по ссылке и языку |

## Возможности

- Надёжный и воспроизводимый поиск библейских текстов
- Поддержка нескольких языков (как минимум английский)
- Поиск стихов по ссылкам
- Совместимость с OpenAI completions API
- Интеграция с Claude Desktop через MCP
- Деплой в Docker контейнере
- Swagger API документация

## Примеры использования

```
Get verses by reference: Gen.1.1, Gen.2.1 in English
```

```
Look up biblical passages for interpretation and understanding
```

```
Research biblical text with reproducible results
```

## Ресурсы

- [GitHub Repository](https://github.com/AdbC99/ai-bible)

## Примечания

Сервер можно использовать напрямую как MCP сервер с Claude Desktop через файл mcp-server.stdio.js или развернуть как Docker контейнер с совместимостью OpenAI completions API. Веб-фронтенд доступен на http://ai-bible.com. Проект включает как MCP сервер, так и Docker wrapper с использованием mcpo. Тестирование API через swagger на http://localhost:8002/docs при локальном запуске.
