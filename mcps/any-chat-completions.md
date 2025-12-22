---
title: Any Chat Completions MCP сервер
description: Интегрирует Claude с любым API Chat Completion, совместимым с OpenAI SDK —
  OpenAI, Perplexity, Groq, xAI, PyroPrompts и другие через единый chat инструмент.
tags:
- AI
- API
- Integration
- Productivity
author: pyroprompts
featured: true
---

Интегрирует Claude с любым API Chat Completion, совместимым с OpenAI SDK — OpenAI, Perplexity, Groq, xAI, PyroPrompts и другие через единый chat инструмент.

## Установка

### NPX

```bash
npx @pyroprompts/any-chat-completions-mcp
```

### Из исходников

```bash
npm install
npm run build
```

### Smithery

```bash
npx -y @smithery/cli install any-chat-completions-mcp-server --client claude
```

## Конфигурация

### Claude Desktop — NPX

```json
{
  "mcpServers": {
    "chat-openai": {
      "command": "npx",
      "args": [
        "@pyroprompts/any-chat-completions-mcp"
      ],
      "env": {
        "AI_CHAT_KEY": "OPENAI_KEY",
        "AI_CHAT_NAME": "OpenAI",
        "AI_CHAT_MODEL": "gpt-4o",
        "AI_CHAT_BASE_URL": "https://api.openai.com/v1"
      }
    }
  }
}
```

### Claude Desktop — из исходников

```json
{
  "mcpServers": {
    "chat-openai": {
      "command": "node",
      "args": [
        "/path/to/any-chat-completions-mcp/build/index.js"
      ],
      "env": {
        "AI_CHAT_KEY": "OPENAI_KEY",
        "AI_CHAT_NAME": "OpenAI",
        "AI_CHAT_MODEL": "gpt-4o",
        "AI_CHAT_BASE_URL": "https://api.openai.com/v1"
      }
    }
  }
}
```

### Claude Desktop — несколько провайдеров

```json
{
  "mcpServers": {
    "chat-pyroprompts": {
      "command": "node",
      "args": [
        "/path/to/any-chat-completions-mcp/build/index.js"
      ],
      "env": {
        "AI_CHAT_KEY": "PYROPROMPTS_KEY",
        "AI_CHAT_NAME": "PyroPrompts",
        "AI_CHAT_MODEL": "ash",
        "AI_CHAT_BASE_URL": "https://api.pyroprompts.com/openaiv1"
      }
    },
    "chat-perplexity": {
      "command": "node",
      "args": [
        "/path/to/any-chat-completions-mcp/build/index.js"
      ],
      "env": {
        "AI_CHAT_KEY": "PERPLEXITY_KEY",
        "AI_CHAT_NAME": "Perplexity",
        "AI_CHAT_MODEL": "sonar",
        "AI_CHAT_BASE_URL": "https://api.perplexity.ai"
      }
    },
    "chat-openai": {
      "command": "node",
      "args": [
        "/path/to/any-chat-completions-mcp/build/index.js"
      ],
      "env": {
        "AI_CHAT_KEY": "OPENAI_KEY",
        "AI_CHAT_NAME": "OpenAI",
        "AI_CHAT_MODEL": "gpt-4o",
        "AI_CHAT_BASE_URL": "https://api.openai.com/v1"
      }
    }
  }
}
```

### LibreChat

```json
chat-perplexity:
  type: stdio
  command: npx
  args:
    - -y
    - @pyroprompts/any-chat-completions-mcp
  env:
    AI_CHAT_KEY: "pplx-012345679"
    AI_CHAT_NAME: Perplexity
    AI_CHAT_MODEL: sonar
    AI_CHAT_BASE_URL: "https://api.perplexity.ai"
    PATH: '/usr/local/bin:/usr/bin:/bin'
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `chat` | Передаёт вопрос настроенному AI Chat провайдеру, совместимому с OpenAI SDK |

## Возможности

- Подключение Claude к любому API, совместимому с OpenAI SDK
- Поддержка множества провайдеров (OpenAI, Perplexity, Groq, xAI, PyroPrompts)
- Настройка нескольких провайдеров одновременно
- Совместимость с Claude Desktop и LibreChat
- Реализация на TypeScript

## Переменные окружения

### Обязательные
- `AI_CHAT_KEY` — API ключ для сервиса chat completion
- `AI_CHAT_NAME` — отображаемое имя провайдера
- `AI_CHAT_MODEL` — модель для chat completions
- `AI_CHAT_BASE_URL` — базовый URL для API chat completion

## Ресурсы

- [GitHub Repository](https://github.com/pyroprompts/any-chat-completions-mcp)

## Примечания

Поддерживает режим разработки с авто-пересборкой через 'npm run watch'. Отладка доступна через MCP Inspector с командой 'npm run inspector'. Спонсировано PyroPrompts — используйте код 'CLAUDEANYCHAT' для получения 20 бесплатных кредитов автоматизации.
