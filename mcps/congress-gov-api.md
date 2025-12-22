---
title: Congress.gov API MCP сервер
description: Неофициальный MCP сервер для Congress.gov API, который позволяет запрашивать данные в реальном времени о деятельности Конгресса США, законопроектах, поправках, членах, комитетах и многом другом.
tags:
- API
- Analytics
- Database
- Integration
- Productivity
author: Community
featured: false
install_command: npx -y @smithery/cli install @AshwinSundar/congress_gov_mcp --client
  claude
---

Неофициальный MCP сервер для Congress.gov API, который позволяет запрашивать данные в реальном времени о деятельности Конгресса США, законопроектах, поправках, членах, комитетах и многом другом.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @AshwinSundar/congress_gov_mcp --client claude
```

### Ручная установка

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
git clone http://github.com/AshwinSundar/congress_gov_mcp
cd congress_gov_mcp
uv sync
cp .env.template .env
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "congress_gov_mcp": {
      "command": "/absolute_path/to/uv",
      "args": [
        "run",
        "/absolute_path_to/congress_gov_mcp/server.py"
      ]
    }
  }
}
```

### Claude Code

```json
{
  "mcpServers": {
    "congress_gov_mcp": {
      "command": "uv",
      "args": [
        "run",
        "/absolute_path_to/congress_gov_mcp/server.py"
      ]
    }
  }
}
```

## Возможности

- Доступ к законопроектам, поправкам и резюме конгресса
- Поиск информации о членах и комитетах
- Данные о отчетах комитетов, документах, встречах и слушаниях
- Записи голосований Палаты представителей и Сената
- Доступ к протоколам Конгресса (ежедневным и переплетенным)
- Коммуникации Палаты представителей и Сената
- Информация о номинациях и договорах
- Доступ к отчетам CRS

## Переменные окружения

### Обязательные
- `CONGRESS_GOV_API_KEY` - API ключ для доступа к Congress.gov API

## Примеры использования

```
Ever wonder what our (US) Congress is up to?
```

```
Ask the US Congress API yourself
```

## Ресурсы

- [GitHub Repository](https://github.com/AshwinSundar/congress_gov_mcp)

## Примечания

Требуется API ключ Congress.gov с https://api.congress.gov/sign-up/. Дорожная карта показывает обширное покрытие API с множеством уже реализованных эндпоинтов и дополнительными подэндпоинтами, запланированными для будущих релизов.