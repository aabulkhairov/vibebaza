---
title: DeepSeek MCP сервер
description: Model Context Protocol (MCP) сервер, который интегрирует мощные языковые модели DeepSeek (включая модель рассуждений R1) с MCP-совместимыми приложениями, с поддержкой анонимного прокси и многоходовых разговоров.
tags:
- AI
- API
- Integration
- Productivity
author: DMontgomery40
featured: true
---

Model Context Protocol (MCP) сервер, который интегрирует мощные языковые модели DeepSeek (включая модель рассуждений R1) с MCP-совместимыми приложениями, с поддержкой анонимного прокси и многоходовых разговоров.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @dmontgomery40/deepseek-mcp-server --client claude
```

### NPM Global

```bash
npm install -g deepseek-mcp-server
```

### NPX Direct

```bash
npx -y deepseek-mcp-server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "deepseek": {
      "command": "npx",
      "args": [
        "-y",
        "deepseek-mcp-server"
      ],
      "env": {
        "DEEPSEEK_API_KEY": "your-api-key"
      }
    }
  }
}
```

## Возможности

- Анонимное использование прокси для доступа к DeepSeek API
- Автоматическое переключение модели с R1 на V3 при необходимости
- Поддержка многоходовых разговоров с полной историей сообщений
- Обнаружение ресурсов для доступных моделей и конфигураций
- Пользовательский выбор модели (deepseek-reasoner/deepseek-chat)
- Контроль температуры (0.0 - 2.0)
- Настройка лимита максимальных токенов
- Top P сэмплирование (0.0 - 1.0)
- Штраф за присутствие (-2.0 - 2.0)
- Штраф за частоту (-2.0 - 2.0)

## Переменные окружения

### Обязательные
- `DEEPSEEK_API_KEY` - Ваш DeepSeek API ключ для аутентификации

## Примеры использования

```
What models are available?
```

```
What configuration options do I have?
```

```
What is the current temperature setting?
```

```
Start a multi-turn conversation. With the following settings: model: 'deepseek-chat', make it not too creative, and allow 8000 tokens.
```

```
use deepseek-reasoner
```

## Ресурсы

- [GitHub Repository](https://github.com/DMontgomery40/deepseek-mcp-server)

## Примечания

Сервер использует модель R1 от DeepSeek (deepseek-reasoner) по умолчанию для производительности рассуждений на современном уровне. V3 (deepseek-chat) рекомендуется для общего использования благодаря скорости и эффективности токенов. Поддержка многоходовых разговоров полезна для обучения/тонкой настройки open source моделей и сложных взаимодействий, требующих сохранения контекста. Может быть протестирован локально с помощью инструмента MCP Inspector.