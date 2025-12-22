---
title: Goodnews MCP сервер
description: MCP Goodnews — это сервер, который получает позитивные и воодушевляющие новостные статьи из NewsAPI и использует Cohere LLM для ранжирования и возврата топовых новостей на основе позитивного настроения.
tags:
- AI
- Media
- API
- Analytics
- Search
author: VectorInstitute
featured: false
---

MCP Goodnews — это сервер, который получает позитивные и воодушевляющие новостные статьи из NewsAPI и использует Cohere LLM для ранжирования и возврата топовых новостей на основе позитивного настроения.

## Установка

### Из исходного кода

```bash
git clone https://github.com/VectorInstitute/mcp-goodnews.git
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "Goodnews": {
      "command": "<absolute-path-to-bin>/uv",
      "args": [
        "--directory",
        "<absolute-path-to-cloned-repo>/mcp-goodnews/src/mcp_goodnews",
        "run",
        "server.py"
      ],
      "env": {
        "NEWS_API_KEY": "<newsapi-api-key>",
        "COHERE_API_KEY": "<cohere-api-key>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `fetch_list_of_goodnews` | Получает и возвращает кураторский список позитивных новостных статей |

## Возможности

- Получение новостных статей из NewsAPI
- Использование Cohere LLM для анализа настроения в режиме zero-shot
- Ранжирование статей на основе баллов позитивного настроения
- Возврат топовых позитивных новостей
- Фокус на позитивном и воодушевляющем новостном контенте

## Переменные окружения

### Обязательные
- `NEWS_API_KEY` - API ключ для NewsAPI для получения новостных статей
- `COHERE_API_KEY` - API ключ для Cohere LLM для выполнения анализа настроения

## Примеры использования

```
Покажи мне хорошие новости за сегодня.
```

```
Что позитивного произошло в мире на этой неделе?
```

```
Дай мне воодушевляющие новости о науке.
```

## Ресурсы

- [GitHub Repository](https://github.com/VectorInstitute/mcp-goodnews)

## Примечания

Требует uv Python Project and Package Manager. Вдохновлен проектом GoodnewsFirst, но использует современные LLM для ранжирования настроения вместо традиционных методов.