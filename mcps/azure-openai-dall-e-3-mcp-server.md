---
title: Azure OpenAI DALL-E 3 MCP сервер
description: MCP сервер, который обеспечивает мост между возможностями генерации изображений DALL-E 3 от Azure OpenAI и MCP клиентами, позволяя создавать изображения из текста через Model Context Protocol.
tags:
- AI
- Media
- API
- Cloud
- Integration
author: jacwu
featured: false
---

MCP сервер, который обеспечивает мост между возможностями генерации изображений DALL-E 3 от Azure OpenAI и MCP клиентами, позволяя создавать изображения из текста через Model Context Protocol.

## Установка

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### MCP клиент

```json
{
  "mcpServers": {
    "dalle3": {
      "command": "node",
      "args": [
        "path/to/mcp-server-aoai-dalle3/build/index.js"
      ],
      "env": {
        "AZURE_OPENAI_ENDPOINT": "<endpoint>",
        "AZURE_OPENAI_API_KEY": "<key>",
        "AZURE_OPENAI_DEPLOYMENT_NAME": "<deployment>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate_image` | Генерирует изображения с помощью Azure OpenAI DALL-E 3 с настраиваемыми параметрами размера, качества и стиля |
| `download_image` | Загружает сгенерированные изображения в локальное хранилище с указанным именем файла и путем к директории |

## Возможности

- Генерация изображений с помощью Azure OpenAI DALL-E 3
- Настраиваемые размеры изображений (1024x1024, 1792x1024, 1024x1792)
- Опции качества (standard, hd)
- Опции стиля (vivid, natural)
- Загрузка сгенерированных изображений в локальное хранилище

## Переменные окружения

### Обязательные
- `AZURE_OPENAI_ENDPOINT` - URL эндпоинта для вашего Azure OpenAI ресурса
- `AZURE_OPENAI_API_KEY` - API ключ для вашего Azure OpenAI ресурса

### Опциональные
- `AZURE_OPENAI_DEPLOYMENT_NAME` - Название деплоя DALL-E 3 в вашем Azure OpenAI ресурсе
- `OPENAI_API_VERSION` - Версия API для использования

## Ресурсы

- [GitHub Repository](https://github.com/jacwu/mcp-server-aoai-dalle3)

## Примечания

Название деплоя по умолчанию - 'dalle3', а версия API по умолчанию - '2024-02-15-preview'. Сервер требует сборки из исходного кода с помощью npm.