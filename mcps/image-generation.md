---
title: Image Generation MCP сервер
description: Этот MCP сервер предоставляет возможности генерации изображений с использованием модели Replicate Flux, позволяя пользователям создавать изображения из текстовых подсказок с различными опциями настройки.
tags:
- AI
- Media
- API
author: Community
featured: false
install_command: npx -y @smithery/cli install @GongRzhe/Image-Generation-MCP-Server
  --client claude
---

Этот MCP сервер предоставляет возможности генерации изображений с использованием модели Replicate Flux, позволяя пользователям создавать изображения из текстовых подсказок с различными опциями настройки.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @GongRzhe/Image-Generation-MCP-Server --client claude
```

### NPX (без локальной настройки)

```bash
# Установка не требуется - npx всё сделает сам
```

### Глобальный NPM

```bash
npm install -g @gongrzhe/image-gen-server
```

### Локальный NPM

```bash
npm install @gongrzhe/image-gen-server
```

## Конфигурация

### Конфигурация Claude Desktop с NPX

```json
{
  "mcpServers": {
    "image-gen": {
      "command": "npx",
      "args": ["@gongrzhe/image-gen-server"],
      "env": {
        "REPLICATE_API_TOKEN": "your-replicate-api-token",
        "MODEL": "alternative-model-name"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### Конфигурация Claude Desktop с локальной установкой

```json
{
  "mcpServers": {
    "image-gen": {
      "command": "node",
      "args": ["/path/to/image-gen-server/build/index.js"],
      "env": {
        "REPLICATE_API_TOKEN": "your-replicate-api-token",
        "MODEL": "alternative-model-name"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate_image` | Генерирует изображения с помощью модели Flux на основе текстовых подсказок с настраиваемыми параметрами, такими как соотношение сторон... |

## Возможности

- Генерация изображений с использованием модели Replicate Flux
- Настраиваемые соотношения сторон
- Множественные форматы вывода (webp, jpg, png)
- Воспроизводимая генерация с параметром seed
- Генерация нескольких изображений (1-4) за один запрос
- Прямая интеграция с Claude Desktop

## Переменные окружения

### Обязательные
- `REPLICATE_API_TOKEN` - Ваш токен Replicate API для аутентификации

### Опциональные
- `MODEL` - Модель Replicate для генерации изображений. По умолчанию "black-forest-labs/flux-schnell"

## Примеры использования

```
Создай красивый закат над горами
```

```
Создай изображения с определёнными соотношениями сторон, например 16:9
```

```
Создай несколько вариаций одной и той же подсказки
```

```
Создай воспроизводимые изображения, используя значения seed
```

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/Image-Generation-MCP-Server)

## Примечания

Требуется аккаунт Replicate и токен API. Сервер поддерживает параметры конфигурации, такие как 'disabled' для управления состоянием сервера и 'autoApprove' для автоматического одобрения выполнения инструментов. Использует TypeScript для примеров использования инструментов.