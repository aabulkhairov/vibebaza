---
title: Voice Status Report MCP сервер
description: MCP сервер, который обеспечивает голосовые обновления статуса с использованием API синтеза речи OpenAI, позволяя языковым моделям общаться с пользователями через короткие голосовые сообщения о прогрессе задач и подтверждениях.
tags:
- AI
- Productivity
- API
- Integration
- Code
author: Community
featured: false
---

MCP сервер, который обеспечивает голосовые обновления статуса с использованием API синтеза речи OpenAI, позволяя языковым моделям общаться с пользователями через короткие голосовые сообщения о прогрессе задач и подтверждениях.

## Установка

### UVX

```bash
uvx voice-status-report-mcp-server
```

### Командная строка с опциями

```bash
voice-status-report-mcp-server --ding --voice nova
voice-status-report-mcp-server --speed 2.0
voice-status-report-mcp-server --instructions "Voice should be confident and authoritative"
```

## Конфигурация

### Claude Desktop базовая

```json
{
  "mcpServers": {
    "voice-status-report": {
      "command": "uvx",
      "args": [
        "voice-status-report-mcp-server"
      ],
      "env": {
        "OPENAI_API_KEY": "YOUR_OPENAI_API_KEY"
      }
    }
  }
}
```

### Claude Desktop с опциями

```json
{
  "mcpServers": {
    "voice-status-report-mcp-server": {
      "command": "uvx",
      "args": [
        "voice-status-report-mcp-server",
        "--ding",
        "--voice", "nova",
        "--speed", "3.0",
        "--instructions", "Voice should be confident and authoritative"
      ],
      "env": {
        "OPENAI_API_KEY": "YOUR_OPENAI_API_KEY"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `summarize` | Преобразует предоставленный текст в речь с использованием TTS API OpenAI и воспроизводит его для пользователя. Это и... |

## Возможности

- Голосовые обновления статуса с использованием API синтеза речи OpenAI
- Отчеты о прогрессе для задач и подтверждений
- Настраиваемые варианты голоса (alloy, ash, coral, echo, fable, onyx, nova, sage, shimmer)
- Регулируемая скорость речи (0.5-4.0)
- Опциональный звуковой сигнал перед голосовыми сообщениями
- Пользовательские инструкции для голоса для модели TTS
- Полная комплектация с встроенными описаниями инструментов

## Переменные окружения

### Обязательные
- `OPENAI_API_KEY` - Ваш API ключ OpenAI для доступа к сервису синтеза речи

## Примеры использования

```
Added a new function to handle user authentication
```

```
Fixed the bug in the login form
```

```
Created a new file for the API client
```

```
Added OpenAI TTS documentation link
```

## Ресурсы

- [GitHub Repository](https://github.com/tomekkorbak/voice-status-report-mcp-server)

## Примечания

Особенно полезно при работе с Cursor или Claude code - вы можете дать агенту задачу, пойти заняться чем-то другим, но продолжать получать отчеты о статусе прогресса агента и уведомления о завершении. По умолчанию используется голос 'coral' со скоростью 4.0, а звуковой сигнал отключен.