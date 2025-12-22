---
title: Dappier MCP сервер
description: Обеспечивает быстрый, бесплатный поиск в реальном времени и доступ к премиальным данным от проверенных медиа-брендов — новости, финансовые рынки, спорт, развлечения, погода и многое другое через AI-модели.
tags:
- Search
- Finance
- Media
- API
- AI
author: DappierAI
featured: false
---

Обеспечивает быстрый, бесплатный поиск в реальном времени и доступ к премиальным данным от проверенных медиа-брендов — новости, финансовые рынки, спорт, развлечения, погода и многое другое через AI-модели.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @DappierAI/dappier-mcp --client claude
```

### UV (MacOS/Linux)

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### UV (Windows)

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "dappier": {
      "command": "uvx",
      "args": ["dappier-mcp"],
      "env": {
        "DAPPIER_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "dappier": {
      "command": "uvx",
      "args": ["dappier-mcp"],
      "env": {
        "DAPPIER_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

### Windsurf

```json
{
  "mcpServers": {
    "dappier": {
      "command": "uvx",
      "args": ["dappier-mcp"],
      "env": {
        "DAPPIER_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

## Возможности

- Поиск в реальном времени с AI-индексацией
- Свежие новости из мировых источников
- Прогнозы погоды и локальные обновления
- Уведомления о поездках и информация о рейсах
- Инсайты фондового рынка с ценами в реальном времени
- Финансовые новости и обновления компаний
- Торговые сигналы и рыночные тренды
- Спортивные новости и обзоры игр
- Контент о стиле жизни и советы по здоровью
- Помощь по уходу за домашними животными — собаками и кошками

## Переменные окружения

### Обязательные
- `DAPPIER_API_KEY` - API ключ для доступа к сервисам Dappier, получается на platform.dappier.com

## Примеры использования

```
Search for breaking news about current events
```

```
Get real-time stock prices and market analysis
```

```
Find weather forecasts for travel planning
```

```
Discover trending topics and viral content
```

```
Get sports updates and game results
```

## Ресурсы

- [GitHub Repository](https://github.com/DappierAI/dappier-mcp)

## Примечания

Требует API ключ с платформы Dappier. Поддерживает множество AI-моделей для разных типов контента. Отладка через MCP inspector: 'npx @modelcontextprotocol/inspector uvx dappier-mcp'. Изучите доступные модели данных на marketplace.dappier.com.