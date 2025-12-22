---
title: ChatMCP
description: Кроссплатформенное десктопное приложение на основе Electron с чистым минималистичным интерфейсом для подключения и взаимодействия с различными LLM через MCP (Model Context Protocol).
tags:
- AI
- Productivity
- Integration
- Code
author: AI-QL
featured: true
---

Кроссплатформенное десктопное приложение на основе Electron с чистым минималистичным интерфейсом для подключения и взаимодействия с различными LLM через MCP (Model Context Protocol).

## Установка

### Из исходного кода

```bash
git clone [repository]
npm install
npm start
```

### Сборка приложения

```bash
npm run build-app
```

## Конфигурация

### Конфигурация MCP сервера

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "node",
      "args": [
        "node_modules/@modelcontextprotocol/server-filesystem/dist/index.js",
        "D:/Github/mcp-test"
      ]
    }
  }
}
```

### Конфигурация GPT API

```json
{
  "chatbotStore": {
    "apiKey": "",
    "url": "https://api.aiql.com",
    "path": "/v1/chat/completions",
    "model": "gpt-4o-mini",
    "max_tokens_value": "",
    "mcp": true
  },
  "defaultChoiceStore": {
    "model": [
      "gpt-4o-mini",
      "gpt-4o",
      "gpt-4",
      "gpt-4-turbo"
    ]
  }
}
```

### Конфигурация Qwen API

```json
{
  "chatbotStore": {
    "apiKey": "",
    "url": "https://dashscope.aliyuncs.com/compatible-mode",
    "path": "/v1/chat/completions",
    "model": "qwen-turbo",
    "max_tokens_value": "",
    "mcp": true
  },
  "defaultChoiceStore": {
    "model": [
      "qwen-turbo",
      "qwen-plus",
      "qwen-max"
    ]
  }
}
```

### Конфигурация DeepInfra

```json
{
  "chatbotStore": {
    "apiKey": "",
    "url": "https://api.deepinfra.com",
    "path": "/v1/openai/chat/completions",
    "model": "meta-llama/Meta-Llama-3.1-70B-Instruct",
    "max_tokens_value": "32000",
    "mcp": true
  },
  "defaultChoiceStore": {
    "model": [
      "meta-llama/Meta-Llama-3.1-70B-Instruct",
      "meta-llama/Meta-Llama-3.1-405B-Instruct",
      "meta-llama/Meta-Llama-3.1-8B-Instruct"
    ]
  }
}
```

## Возможности

- Кроссплатформенная совместимость: поддержка Linux, macOS и Windows
- Гибкая лицензия Apache-2.0: позволяет легко модифицировать и создавать кастомные десктопные приложения
- Динамическая конфигурация LLM: совместимость со всеми LLM, поддерживаемыми OpenAI SDK
- Управление несколькими клиентами: настройка и управление несколькими клиентами для подключения к нескольким серверам через MCP конфигурацию
- Адаптируемый UI: интерфейс можно извлечь для веб-использования с консистентной логикой взаимодействия
- Мультимодальная поддержка
- Поддержка логических рассуждений и LaTeX
- Визуализация MCP инструментов
- Шаблоны MCP промптов
- Отладка через DevTool

## Переменные окружения

### Опциональные
- `ELECTRON_MIRROR` - зеркальный сайт для загрузки Electron для решения проблем с таймаутами

## Ресурсы

- [GitHub Repository](https://github.com/AI-QL/chat-mcp)

## Примечания

Этот проект эволюционировал в TUUI (Tool Unitary User Interface) — реструктурированное десктопное приложение, оптимизированное для AI-разработки. Приложение включает предустановленные server-everything, server-filesystem и server-puppeteer для тестирования. Пользователям Windows может потребоваться использовать 'node' вместо 'npx' в config.json из-за проблем со spawn.