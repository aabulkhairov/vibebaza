---
title: Skyvern MCP сервер
description: MCP сервер от Skyvern помогает подключать AI-приложения к браузеру, позволяя им заполнять формы, скачивать файлы, исследовать информацию в интернете и многое другое.
tags:
- Browser
- Web Scraping
- AI
- Integration
- Productivity
author: Skyvern-AI
featured: true
---

MCP сервер от Skyvern помогает подключать AI-приложения к браузеру, позволяя им заполнять формы, скачивать файлы, исследовать информацию в интернете и многое другое.

## Установка

### Установка через Pip

```bash
pip install skyvern
```

### Настройка конфигурации

```bash
skyvern init
```

### Запуск локального сервера

```bash
skyvern run server
```

## Конфигурация

### Общая конфигурация MCP

```json
{
  "mcpServers": {
    "Skyvern": {
      "env": {
        "SKYVERN_BASE_URL": "https://api.skyvern.com", # "http://localhost:8000" если запускаете локально
        "SKYVERN_API_KEY": "YOUR_SKYVERN_API_KEY" # найдите локальный SKYVERN_API_KEY в .env файле после выполнения `skyvern init` или в консоли Skyvern Cloud
      },
      "command": "PATH_TO_PYTHON",
      "args": [
        "-m",
        "skyvern",
        "run",
        "mcp"
      ]
    }
  }
}
```

## Возможности

- Заполнение форм в браузере
- Скачивание файлов с веб-сайтов
- Исследование информации в интернете
- Подключение к Skyvern Cloud или локальному серверу
- Поддержка множества AI-приложений (Cursor, Windsurf, Claude Desktop)

## Переменные окружения

### Обязательные
- `SKYVERN_BASE_URL` - базовый URL для Skyvern API (https://api.skyvern.com для облака, http://localhost:8000 для локального)
- `SKYVERN_API_KEY` - API ключ для аутентификации Skyvern (находится в .env файле после init или в консоли Skyvern Cloud)

## Примеры использования

```
Look up the top Hackernews posts today
```

```
Look up the top programming jobs in your area
```

```
Do a form 5500 search and download some files
```

## Ресурсы

- [GitHub Repository](https://github.com/Skyvern-AI/skyvern)

## Примечания

⚠️ ТРЕБОВАНИЕ: Skyvern на данный момент работает только в среде Python 3.11. Вы можете подключиться либо к Skyvern Cloud (создайте аккаунт на app.skyvern.com), либо запустить локальный сервер Skyvern. Мастер настройки (skyvern init) проведет вас через конфигурацию для поддерживаемых приложений, включая Cursor, Windsurf и Claude Desktop.