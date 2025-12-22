---
title: JSON2Video MCP сервер
description: Реализация сервера Model Context Protocol (MCP) для программного генерирования видео с использованием json2video API, предоставляющая мощные инструменты создания видео и проверки статуса для работы с LLM, агентами или любыми MCP-совместимыми клиентами.
tags:
- Media
- API
- AI
- Productivity
- Integration
author: omergocmen
featured: false
---

Реализация сервера Model Context Protocol (MCP) для программного генерирования видео с использованием json2video API, предоставляющая мощные инструменты создания видео и проверки статуса для работы с LLM, агентами или любыми MCP-совместимыми клиентами.

## Установка

### NPX

```bash
env JSON2VIDEO_API_KEY=your_api_key_here npx -y @omerrgocmen/json2video-mcp
```

### Ручная установка

```bash
npm install -g @omerrgocmen/json2video-mcp
```

### Windows

```bash
cmd /c "set JSON2VIDEO_API_KEY=your_api_key_here && npx -y @omerrgocmen/json2video-mcp"
```

## Конфигурация

### Cursor v0.48.6+ (Command)

```json
Command: env JSON2VIDEO_API_KEY=your_api_key_here npx -y @omerrgocmen/json2video-mcp
```

### Cursor v0.48.6+ (JSON)

```json
{
  "mcpServers": {
    "json2video-mcp": {
      "command": "npx",
      "args": ["-y", "@omerrgocmen/json2video-mcp"],
      "env": {
        "JSON2VIDEO_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Интеграция MCP

```json
{
  "mcpServers": {
    "json2video-mcp": {
      "command": "npx",
      "args": ["-y", "@omerrgocmen/json2video-mcp"],
      "env": {
        "JSON2VIDEO_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate_video` | Создание настраиваемого видеопроекта со сценами и элементами, включая текст, изображения, видео, аудио... |
| `get_video_status` | Проверка статуса или получение результата задачи генерации видео |
| `create_template` | Создание нового шаблона в json2video с заданным именем и опциональным описанием |
| `get_template` | Получение деталей шаблона из json2video по его имени |
| `list_templates` | Список всех доступных шаблонов из json2video |

## Возможности

- Генерация видео с богатой поддержкой сцен и элементов (текст, изображения, видео, аудио, компоненты, субтитры и т.д.)
- Асинхронный рендеринг видео с опросом статуса
- Гибкая, расширяемая JSON схема для видеопроектов
- Создан для легкой интеграции с LLM, агентами автоматизации и MCP-совместимыми инструментами
- Аутентификация по API ключу (через переменные окружения или для каждого запроса)
- Комплексная обработка ошибок и логирование

## Переменные окружения

### Обязательные
- `JSON2VIDEO_API_KEY` - Ваш API ключ json2video. Может быть установлен как переменная окружения или предоставлен для каждого запроса.

## Ресурсы

- [GitHub Repository](https://github.com/omergocmen/json2video-mcp-server)

## Примечания

Генерация видео происходит асинхронно и может занять некоторое время. Если вы столкнулись с ошибкой 'client closed', выполните 'npm i @omerrgocmen/json2video-mcp'. Вы можете получить API ключ на json2video.com. Смотрите https://json2video.com/docs/api/ для полной схемы и дополнительных примеров.