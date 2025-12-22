---
title: Nanana MCP сервер
description: MCP сервер для сервиса генерации изображений Nanana AI на базе модели nano banana от Google Gemini, позволяющий Claude Desktop и другим MCP клиентам генерировать и трансформировать изображения с помощью мощных возможностей искусственного интеллекта.
tags:
- AI
- Media
- API
author: Community
featured: false
---

MCP сервер для сервиса генерации изображений Nanana AI на базе модели nano banana от Google Gemini, позволяющий Claude Desktop и другим MCP клиентам генерировать и трансформировать изображения с помощью мощных возможностей искусственного интеллекта.

## Установка

### Глобальная установка через NPM

```bash
npm install -g @nanana-ai/mcp-server-nano-banana
```

### NPX

```bash
npx -y @nanana-ai/mcp-server-nano-banana
```

### Из исходников

```bash
git clone repository
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "nanana": {
      "command": "npx",
      "args": ["-y", "@nanana-ai/mcp-server-nano-banana"],
      "env": {
        "NANANA_API_TOKEN": "your-api-token-here"
      }
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "nanana": {
      "command": "node",
      "args": ["/path/to/packages/mcp-server/dist/index.js"],
      "env": {
        "NANANA_API_TOKEN": "your-token",
        "NANANA_API_URL": "http://localhost:3000"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `text_to_image` | Генерирует изображение из текстового описания |
| `image_to_image` | Трансформирует существующие изображения на основе текстового описания (поддерживает от 1 до 9 URL изображений) |

## Возможности

- Генерация изображений из текста с помощью модели nano banana от Google Gemini
- Возможности трансформации изображений
- Поддержка множественных входных изображений (от 1 до 9 изображений)
- Интеграция с сервисом Nanana AI
- Система использования на основе кредитов

## Переменные окружения

### Обязательные
- `NANANA_API_TOKEN` - Ваш токен API для Nanana AI

### Опциональные
- `NANANA_API_URL` - Кастомный URL API (по умолчанию https://nanana.app)

## Примеры использования

```
Generate an image of a cute cat wearing a hat
```

```
Transform these images to look like oil paintings: ["https://example.com/image1.jpg"]
```

## Ресурсы

- [GitHub Repository](https://github.com/nanana-app/mcp-server-nano-banana)

## Примечания

Требует токен API из аккаунта nanana.app. Генерация изображений потребляет кредиты с вашего аккаунта Nanana AI. Проверьте баланс кредитов в панели управления на nanana.app/account и купите дополнительные кредиты при необходимости.