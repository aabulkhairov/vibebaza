---
title: jobswithgpt MCP сервер
description: Динамический сервис управления MCP серверами, который создает, запускает и управляет серверами Model Context Protocol в динамическом режиме, а также предоставляет функциональность поиска работы через jobswithgpt с индексацией более 500 тысяч публичных вакансий.
tags:
- Search
- API
- Integration
- Productivity
author: jobswithgpt
featured: false
---

Динамический сервис управления MCP серверами, который создает, запускает и управляет серверами Model Context Protocol в динамическом режиме, а также предоставляет функциональность поиска работы через jobswithgpt с индексацией более 500 тысяч публичных вакансий.

## Установка

### NPX Proxy

```bash
npx -y mcp-remote@latest https://jobswithgpt.com/mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "jobswithgpt": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote@latest",
        "https://jobswithgpt.com/mcp"
      ]
    }
  }
}
```

## Возможности

- Динамический сервис управления MCP серверами
- Создание, запуск и управление MCP серверами в динамическом режиме
- Функционирует как полноценный MCP сервер
- Запускает и управляет другими MCP серверами как дочерними процессами
- Поиск работы через jobswithgpt API
- Индексация более 500 тысяч публичных вакансий
- Постоянно обновляемые данные о вакансиях
- Функциональность автодополнения локаций
- Доступен хостед MCP коннектор

## Примеры использования

```
Find machine learning jobs in san francisco
```

```
First call location_autocomplete to get a geonameid for 'Seattle', then call search_jobs with keywords=['python'] and that geonameid
```

## Ресурсы

- [GitHub Repository](https://github.com/jobswithgpt/mcp)

## Примечания

Доступен как хостед MCP коннектор по адресу https://jobswithgpt.com/mcp для PRO аккаунтов. Бесплатные аккаунты могут использовать proxy конфигурацию. Также поддерживает интеграцию с OpenAI через MCPServerStreamableHttp.