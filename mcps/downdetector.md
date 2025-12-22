---
title: Downdetector MCP сервер
description: MCP сервер, который предоставляет информацию о статусе сервисов и сбоях в реальном времени из Downdetector для различных сервисов и регионов без необходимости аутентификации.
tags:
- Monitoring
- API
- Web Scraping
- Analytics
author: domdomegg
featured: false
---

MCP сервер, который предоставляет информацию о статусе сервисов и сбоях в реальном времени из Downdetector для различных сервисов и регионов без необходимости аутентификации.

## Установка

### Ручная установка .dxt

```bash
1. Download mcp-server-dxt from GitHub Actions
2. Rename .zip to .dxt
3. Double-click .dxt file
4. Click Install in Claude Desktop
```

### NPX

```bash
npx -y downdetector-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "downdetector": {
      "command": "npx",
      "args": [
        "-y",
        "downdetector-mcp"
      ]
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "downdetector": {
      "command": "npx",
      "args": ["-y", "downdetector-mcp"]
    }
  }
}
```

### Cline

```json
{
  "mcpServers": {
    "downdetector": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "downdetector-mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `downdetector` | Получить текущий статус и отчеты о сбоях для любого сервиса, отслеживаемого Downdetector с опциональным dom... |

## Возможности

- Статус сервиса в реальном времени: Получайте актуальные отчеты о статусе для любого сервиса, отслеживаемого Downdetector
- Аутентификация не требуется: Прямой доступ к публичным данным Downdetector
- Глобальное покрытие: Поддержка различных доменов Downdetector (com, uk, it, fr и др.)

## Примеры использования

```
Check if Steam is down right now
```

```
What's the current status of Netflix?
```

```
Get the latest reports for Instagram in the UK
```

```
Show me the recent activity for Discord
```

## Ресурсы

- [GitHub Repository](https://github.com/domdomegg/downdetector-mcp)

## Примечания

Данные поступают из публичного интерфейса Downdetector и могут быть ограничены по частоте запросов. Некоторые домены (особенно .com) могут быть защищены Cloudflare и периодически недоступны. Имена сервисов должны соответствовать тем, что используются в Downdetector (регистр не важен).