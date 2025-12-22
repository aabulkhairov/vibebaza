---
title: Cloudinary MCP сервер
description: Cloudinary MCP сервер предоставляет инструменты для загрузки изображений и видео в Cloudinary через Claude Desktop и совместимые MCP клиенты, возвращая ссылки на медиа и детали.
tags:
- Cloud
- Storage
- Media
- API
- Integration
author: Community
featured: false
---

Cloudinary MCP сервер предоставляет инструменты для загрузки изображений и видео в Cloudinary через Claude Desktop и совместимые MCP клиенты, возвращая ссылки на медиа и детали.

## Установка

### NPX (Рекомендуется)

```bash
npx @felores/cloudinary-mcp-server@latest
```

### Из исходников

```bash
git clone https://github.com/felores/cloudinary-mcp-server.git
cd cloudinary-mcp-server
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "cloudinary": {
      "command": "npx",
      "args": ["@felores/cloudinary-mcp-server@latest"],
      "env": {
        "CLOUDINARY_CLOUD_NAME": "your_cloud_name",
        "CLOUDINARY_API_KEY": "your_api_key",
        "CLOUDINARY_API_SECRET": "your_api_secret"
      }
    }
  }
}
```

### Claude Desktop (Локально)

```json
{
  "mcpServers": {
    "cloudinary": {
      "command": "node",
      "args": ["c:/path/to/cloudinary-mcp-server/dist/index.js"],
      "env": {
        "CLOUDINARY_CLOUD_NAME": "your_cloud_name",
        "CLOUDINARY_API_KEY": "your_api_key",
        "CLOUDINARY_API_SECRET": "your_api_secret"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `upload` | Загружает изображения и видео в Cloudinary с поддержкой путей к файлам, URL или base64 data URI |

## Возможности

- Загрузка изображений и видео в Cloudinary
- Поддержка путей к файлам, URL и base64 data URI
- Назначение пользовательских публичных ID
- Возможность перезаписи ресурсов
- Назначение тегов для загруженных ресурсов
- Указание типа ресурса (image, video, raw)

## Переменные окружения

### Обязательные
- `CLOUDINARY_CLOUD_NAME` - Название вашего облака Cloudinary из консоли Cloudinary
- `CLOUDINARY_API_KEY` - Ваш API ключ Cloudinary из консоли Cloudinary
- `CLOUDINARY_API_SECRET` - Ваш API секрет Cloudinary из консоли Cloudinary

## Примеры использования

```
Загрузить изображение в Cloudinary
```

```
Загрузить видео с пользовательским публичным ID
```

```
Загрузить медиа по URL
```

```
Загрузить и пометить медиа ресурсы тегами
```

## Ресурсы

- [GitHub Repository](https://github.com/felores/cloudinary-mcp-server)

## Примечания

Требует Node.js версии 18 или выше. Конфигурационные файлы находятся в Windows: C:\Users\NAME\AppData\Roaming\Claude или macOS: ~/Library/Application Support/Claude/. Также доступны через Claude Desktop > Settings > Developer > Edit Config.