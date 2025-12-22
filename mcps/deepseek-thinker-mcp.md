---
title: deepseek-thinker-mcp сервер
description: MCP сервер, который предоставляет доступ к процессам рассуждения и мыслительным процессам Deepseek, поддерживает как режим OpenAI API, так и интеграцию с локальным сервером Ollama.
tags:
- AI
- API
- Integration
- Analytics
author: ruixingshi
featured: false
---

MCP сервер, который предоставляет доступ к процессам рассуждения и мыслительным процессам Deepseek, поддерживает как режим OpenAI API, так и интеграцию с локальным сервером Ollama.

## Установка

### NPX

```bash
npx -y deepseek-thinker-mcp
```

### Из исходного кода

```bash
npm install
npm run build
node build/index.js
```

## Конфигурация

### Claude Desktop - режим OpenAI API

```json
{
  "mcpServers": {
    "deepseek-thinker": {
      "command": "npx",
      "args": [
        "-y",
        "deepseek-thinker-mcp"
      ],
      "env": {
        "API_KEY": "<Your API Key>",
        "BASE_URL": "<Your Base URL>"
      }
    }
  }
}
```

### Claude Desktop - режим Ollama

```json
{
  "mcpServers": {
    "deepseek-thinker": {
      "command": "npx",
      "args": [
        "-y",
        "deepseek-thinker-mcp"
      ],
      "env": {
        "USE_OLLAMA": "true"
      }
    }
  }
}
```

### Конфигурация локального сервера

```json
{
  "mcpServers": {
    "deepseek-thinker": {
      "command": "node",
      "args": [
        "/your-path/deepseek-thinker-mcp/build/index.js"
      ],
      "env": {
        "API_KEY": "<Your API Key>",
        "BASE_URL": "<Your Base URL>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-deepseek-thinker` | Выполняет рассуждение с использованием модели Deepseek со структурированным текстовым ответом, содержащим процесс рассуждения... |

## Возможности

- Поддержка двух режимов: режим OpenAI API и локальный режим Ollama
- Захватывает процесс мышления Deepseek
- Предоставляет вывод рассуждений
- Сфокусированные возможности рассуждения

## Переменные окружения

### Опциональные
- `API_KEY` - Ваш OpenAI API ключ (для режима OpenAI API)
- `BASE_URL` - Базовый URL API (для режима OpenAI API)
- `USE_OLLAMA` - Установите в 'true' для использования локального режима Ollama

## Ресурсы

- [GitHub Repository](https://github.com/ruixingshi/deepseek-thinker-mcp)

## Примечания

Создан с использованием TypeScript, @modelcontextprotocol/sdk, OpenAI API, Ollama и Zod для валидации параметров. Могут возникать ошибки таймаута, когда Deepseek API отвечает медленно или вывод содержимого рассуждений слишком длинный. Лицензируется под MIT License.