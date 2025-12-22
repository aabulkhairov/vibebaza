---
title: RedNote MCP сервер
description: MCP сервер для доступа к контенту RedNote (XiaoHongShu), обеспечивающий поиск и получение заметок/постов с китайской социальной медиа платформы.
tags:
- Web Scraping
- Search
- Media
- API
- Browser
author: iFurySt
featured: true
---

MCP сервер для доступа к контенту RedNote (XiaoHongShu), обеспечивающий поиск и получение заметок/постов с китайской социальной медиа платформы.

## Установка

### Глобальная установка через NPM

```bash
npm install -g rednote-mcp
```

### Из исходного кода

```bash
git clone https://github.com/ifuryst/rednote-mcp.git
cd rednote-mcp
npm install
npm install -g .
```

### Прямой запуск из исходного кода

```bash
npm run dev -- init
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "RedNote MCP": {
      "command": "rednote-mcp",
      "args": [
        "--stdio"
      ]
    }
  }
}
```

### Cursor с NPX

```json
{
  "mcpServers": {
    "RedNote MCP": {
      "command": "npx",
      "args": [
        "rednote-mcp",
        "--stdio"
      ]
    }
  }
}
```

## Возможности

- Управление аутентификацией с сохранением Cookie
- Поиск заметок по ключевым словам
- Инструмент инициализации через командную строку
- Доступ к контенту заметок через URL
- В будущем: доступ к контенту комментариев через URL

## Ресурсы

- [GitHub Repository](https://github.com/ifuryst/rednote-mcp)

## Примечания

Требует установки playwright (npx playwright install) и первоначальной настройки входа через 'rednote-mcp init'. Cookies сохраняются в ~/.mcp/rednote/cookies.json. При первом использовании требуется ручной вход через окно браузера, которое открывается автоматически.