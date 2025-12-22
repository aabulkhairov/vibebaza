---
title: Vectara MCP сервер
description: Предоставляет агентным приложениям доступ к быстрому и надёжному RAG с пониженным количеством галлюцинаций через платформу Vectara's Trusted RAG с использованием протокола MCP.
tags:
- AI
- Search
- Vector Database
- API
- Analytics
author: Community
featured: false
---

Предоставляет агентным приложениям доступ к быстрому и надёжному RAG с пониженным количеством галлюцинаций через платформу Vectara's Trusted RAG с использованием протокола MCP.

## Установка

### PyPI

```bash
pip install vectara-mcp
```

### HTTP Transport (по умолчанию)

```bash
python -m vectara_mcp
```

### STDIO Transport

```bash
python -m vectara_mcp --stdio
```

### Кастомная конфигурация

```bash
python -m vectara_mcp --host 0.0.0.0 --port 8080
```

### SSE Transport

```bash
python -m vectara_mcp --transport sse --path /sse
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "Vectara": {
      "command": "python",
      "args": ["-m", "vectara_mcp", "--stdio"],
      "env": {
        "VECTARA_API_KEY": "your-api-key"
      }
    }
  }
}
```

### Claude Desktop (uv)

```json
{
  "mcpServers": {
    "Vectara": {
      "command": "uv",
      "args": ["tool", "run", "vectara-mcp", "--stdio"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `setup_vectara_api_key` | Настройка и валидация вашего Vectara API ключа для сессии (одноразовая настройка) |
| `clear_vectara_api_key` | Очистка сохранённого API ключа из памяти сервера |
| `ask_vectara` | Выполнение RAG запроса через Vectara, возвращает результаты поиска с сгенерированным ответом |
| `search_vectara` | Выполнение семантического поискового запроса через Vectara, без генерации |
| `correct_hallucinations` | Выявление и исправление галлюцинаций в сгенерированном тексте с помощью VHC от Vectara (Vectara Hallucination ... |
| `eval_factual_consistency` | Оценка фактической согласованности сгенерированного текста с исходными документами с использованием специального... |

## Возможности

- Несколько режимов транспорта: HTTP (по умолчанию), SSE и STDIO
- Встроенная аутентификация через bearer токены для HTTP/SSE
- Ограничение скорости (100 запросов в минуту по умолчанию)
- CORS защита с настраиваемой валидацией источников
- RAG запросы с сгенерированными ответами
- Семантический поиск без генерации
- Детекция и исправление галлюцинаций
- Оценка фактической согласованности
- Безопасность по умолчанию с поддержкой HTTPS
- Потоковая передача в реальном времени с Server-Sent Events

## Переменные окружения

### Обязательные
- `VECTARA_API_KEY` - Ваш Vectara API ключ

### Опциональные
- `VECTARA_AUTHORIZED_TOKENS` - Дополнительные токены авторизации (через запятую)
- `VECTARA_ALLOWED_ORIGINS` - Разрешённые CORS источники (через запятую)
- `VECTARA_TRANSPORT` - Режим транспорта по умолчанию
- `VECTARA_AUTH_REQUIRED` - Принудительная аутентификация (true/false)

## Примеры использования

```
Who is Amr Awadallah?
```

```
What events are happening in NYC?
```

```
Check this text for hallucinations against these source documents
```

```
Evaluate the factual consistency of this generated text
```

## Ресурсы

- [GitHub Repository](https://github.com/vectara/vectara-mcp)

## Примечания

Совместим с Claude Desktop и любыми MCP клиентами. Требует STDIO транспорт для Claude Desktop. Имеет несколько режимов безопасности, для продакшена рекомендуется HTTP транспорт. Включает возможности исправления галлюцинаций и оценки фактической согласованности.