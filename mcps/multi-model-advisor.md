---
title: Multi-Model Advisor MCP сервер
description: MCP сервер, который опрашивает несколько моделей Ollama и объединяет их ответы, предоставляя разнообразные AI-перспективы на один вопрос через подход "совета экспертов".
tags:
- AI
- Integration
- Productivity
author: Community
featured: false
---

MCP сервер, который опрашивает несколько моделей Ollama и объединяет их ответы, предоставляя разнообразные AI-перспективы на один вопрос через подход "совета экспертов".

## Установка

### Smithery

```bash
npx -y @smithery/cli install @YuChenSSR/multi-ai-advisor-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/YuChenSSR/multi-ai-advisor-mcp.git
cd multi-ai-advisor-mcp
npm install
npm run build
ollama pull gemma3:1b
ollama pull llama3.2:1b
ollama pull deepseek-r1:1.5b
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "multi-model-advisor": {
      "command": "node",
      "args": ["/absolute/path/to/multi-ai-advisor-mcp/build/index.js"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list-available-models` | Показывает все модели Ollama в вашей системе |
| `query-models` | Опрашивает несколько моделей одним вопросом |

## Возможности

- Опрос нескольких моделей Ollama одним вопросом
- Назначение различных ролей/персон каждой модели
- Просмотр всех доступных моделей Ollama в вашей системе
- Настройка системных промптов для каждой модели
- Конфигурация через переменные окружения
- Бесшовная интеграция с Claude for Desktop

## Переменные окружения

### Опциональные
- `SERVER_NAME` - Название сервера
- `SERVER_VERSION` - Версия сервера
- `DEBUG` - Включить режим отладки
- `OLLAMA_API_URL` - URL для Ollama API
- `DEFAULT_MODELS` - Список моделей по умолчанию через запятую
- `GEMMA_SYSTEM_PROMPT` - Системный промпт для модели Gemma
- `LLAMA_SYSTEM_PROMPT` - Системный промпт для модели Llama
- `DEEPSEEK_SYSTEM_PROMPT` - Системный промпт для модели DeepSeek

## Примеры использования

```
Show me which Ollama models are available on my system
```

```
what are the most important skills for success in today's job market, you can use gemma3:1b, llama3.2:1b, deepseek-r1:1.5b to help you
```

## Ресурсы

- [GitHub Repository](https://github.com/YuChenSSR/multi-ai-advisor-mcp)

## Примечания

Требует установленный и запущенный локально Ollama. Каждая модель может иметь назначенные различные персоны/роли для получения разнообразных перспектив. Поддерживает Node.js 16.x или выше.