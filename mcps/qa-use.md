---
title: qa-use MCP сервер
description: MCP сервер, который предоставляет комплексные возможности автоматизации браузера и QA тестирования, интегрируясь с desplega.ai для автоматического тестирования, мониторинга сессий, пакетного выполнения тестов и интеллектуальных рекомендаций по тестированию с использованием шаблонов AAA фреймворка.
tags:
- Browser
- AI
- Monitoring
- DevOps
- Integration
author: desplega-ai
featured: false
install_command: claude mcp add desplega-qa npx @desplega.ai/qa-use-mcp@latest --env
  QA_USE_API_KEY=your-desplega-ai-api-key
---

MCP сервер, который предоставляет комплексные возможности автоматизации браузера и QA тестирования, интегрируясь с desplega.ai для автоматического тестирования, мониторинга сессий, пакетного выполнения тестов и интеллектуальных рекомендаций по тестированию с использованием шаблонов AAA фреймворка.

## Установка

### NPX (stdio)

```bash
npx @desplega.ai/qa-use-mcp
```

### NPX (HTTP)

```bash
npx @desplega.ai/qa-use-mcp --http --port 3000
```

### NPX (tunnel)

```bash
npx @desplega.ai/qa-use-mcp tunnel
```

### Docker

```bash
FROM node:18-slim

# Install dependencies for Playwright
RUN apt-get update && apt-get install -y \
    libnss3 libatk-bridge2.0-0 libdrm2 libxkbcommon0 \
    libgbm1 libasound2 libxshmfence1 \
    && rm -rf /var/lib/apt/lists/*

# Install qa-use-mcp
RUN npm install -g @desplega.ai/qa-use-mcp

# Expose port
EXPOSE 3000

# Set API key via environment variable
ENV QA_USE_API_KEY=your-api-key-here

# Start in HTTP mode
CMD ["qa-use-mcp", "--http", "--port", "3000"]
```

## Конфигурация

### Standard MCP Client

```json
{
  "mcpServers": {
    "desplega-qa": {
      "command": "npx",
      "args": ["-y", "@desplega.ai/qa-use-mcp@latest"],
      "env": {
        "QA_USE_API_KEY": "your-desplega-ai-api-key"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "desplega-qa": {
      "command": "npx",
      "args": ["-y", "@desplega.ai/qa-use-mcp@latest"],
      "env": {
        "QA_USE_API_KEY": "your-desplega-ai-api-key"
      }
    }
  }
}
```

### Continue

```json
{
  "mcpServers": {
    "desplega-qa": {
      "command": "npx",
      "args": ["-y", "@desplega.ai/qa-use-mcp@latest"],
      "env": {
        "QA_USE_API_KEY": "your-desplega-ai-api-key"
      }
    }
  }
}
```

### Zed

```json
{
  "mcpServers": {
    "desplega-qa": {
      "command": "npx",
      "args": ["-y", "@desplega.ai/qa-use-mcp@latest"],
      "env": {
        "QA_USE_API_KEY": "your-desplega-ai-api-key"
      }
    }
  }
}
```

## Возможности

- Управление браузером: Запуск и контроль экземпляров браузера Playwright с headless/headed режимами
- Туннелирование: Создание публичных туннелей для WebSocket эндпоинтов браузера с использованием localtunnel
- API интеграция: Полная интеграция с desplega.ai API для комплексных QA тестовых рабочих процессов
- Управление сессиями: Создание, мониторинг и контроль множественных QA тестовых сессий с отслеживанием статуса в реальном времени
- Мониторинг прогресса: Уведомления о прогрессе в реальном времени с защитой от таймаутов MCP (максимум 25 секунд на вызов)
- Пакетное выполнение тестов: Запуск множественных автоматизированных тестов одновременно с управлением зависимостями
- Интерактивное выяснение: Интеллектуальные подсказки когда удаленным сессиям нужен пользовательский ввод для продолжения
- Поиск тестов: Поиск и список автоматизированных тестов с пагинацией и фильтрацией
- Аналитика запуска тестов: Просмотр истории выполнения тестов с метриками производительности и оценками нестабильности
- Шаблоны AAA фреймворка: Готовые шаблоны для логина, форм, электронной коммерции, навигации и комплексных тестовых сценариев

## Переменные окружения

### Обязательные
- `QA_USE_API_KEY` - Ваш API ключ desplega.ai для аутентификации

### Опциональные
- `QA_USE_REGION` - Регион для туннельных соединений (например, 'us' для Северной Америки)

## Примеры использования

```
Инициализируйте QA сервер и протестируйте форму логина на https://app.example.com
```

## Ресурсы

- [GitHub Repository](https://github.com/desplega-ai/qa-use)

## Примечания

Сервер поддерживает три режима: stdio (по умолчанию для MCP клиентов), HTTP/SSE (для веб-интеграций), и tunnel (для задач, инициированных бэкендом). Первоначальная настройка требует запуска init_qa_server с interactive=true или предоставления вашего desplega.ai API ключа. Сессии поддерживают до 10 одновременных экземпляров браузера с TTL 30 минут и автоматической очисткой.