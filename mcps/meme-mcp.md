---
title: Meme MCP сервер
description: MCP сервер для генерации мемов с использованием ImgFlip API, который позволяет ИИ-моделям создавать мемы из пользовательских запросов с настраиваемыми шаблонами и текстом.
tags:
- AI
- API
- Media
- Productivity
author: Community
featured: false
---

MCP сервер для генерации мемов с использованием ImgFlip API, который позволяет ИИ-моделям создавать мемы из пользовательских запросов с настраиваемыми шаблонами и текстом.

## Установка

### NPX

```bash
npx -y meme-mcp
```

### Глобальная установка через NPM

```bash
npm install -g meme-mcp
```

## Конфигурация

### Claude Desktop - NPX

```json
{
  "mcpServers": {
    "meme": {
      "command": "npx",
      "args": ["-y", "meme-mcp"],
      "env": {
        "IMGFLIP_USERNAME": "<IMGFLIP USERNAME>",
        "IMGFLIP_PASSWORD": "<IMGFLIP PASSWORD>"
      }
    }
  }
}
```

### Claude Desktop - прямой путь к Node

```json
{
  "mcpServers": {
    "meme": {
      "command": "/Users/<USERNAME>/.nvm/versions/node/v20.18.2/bin/node",
      "args": ["/Users/<USERNAME>/.nvm/versions/node/v20.18.2/lib/node_modules/meme-mcp/dist/index.js"],
      "env": {
        "IMGFLIP_USERNAME": "<IMGFLIP USERNAME>",
        "IMGFLIP_PASSWORD": "<IMGFLIP PASSWORD>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generateMeme` | Генерирует изображения мемов с помощью ImgFlip API с настраиваемым ID шаблона и заполнителями текста |

## Возможности

- Генерация мемов с использованием ImgFlip API
- Поддержка шаблонов мемов с числовыми ID
- Настраиваемый текст для нескольких заполнителей
- Интеграция с ИИ-моделями через MCP

## Переменные окружения

### Обязательные
- `IMGFLIP_USERNAME` - имя пользователя ImgFlip для аутентификации API
- `IMGFLIP_PASSWORD` - пароль ImgFlip для аутентификации API

## Примеры использования

```
Попросите Claude сгенерировать мем для вас
```

## Ресурсы

- [GitHub Repository](https://github.com/lidorshimoni/meme-mcp)

## Примечания

Требуется бесплатный аккаунт ImgFlip для доступа к API. Claude Desktop может потребовать перезапуска после конфигурации. Иконка молотка появляется в поле ввода чата при правильной настройке. Пользователям NVM может потребоваться использовать прямые пути к node из-за проблем с путями npx.