---
title: World Bank data API MCP сервер
description: MCP сервер для взаимодействия с открытым API данных Всемирного банка, позволяющий ИИ-ассистентам просматривать индикаторы и анализировать их для стран, доступных в базе данных World Bank.
tags:
- API
- Analytics
- Database
- Finance
author: anshumax
featured: false
---

MCP сервер для взаимодействия с открытым API данных Всемирного банка, позволяющий ИИ-ассистентам просматривать индикаторы и анализировать их для стран, доступных в базе данных World Bank.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @anshumax/world_bank_mcp_server --client claude
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "world_bank": {
      "command": "uv",
      "args": [
        "--directory", 
        "path/to/world_bank_mcp_server",
        "run",
        "world_bank_mcp_server"
      ]
    }
  }
}
```

## Возможности

- Просмотр доступных стран в открытом API данных World Bank
- Просмотр доступных индикаторов в открытом API данных World Bank
- Анализ индикаторов, таких как сегменты населения, показатели бедности и др., по странам
- Подробное логирование

## Ресурсы

- [GitHub Repository](https://github.com/anshumax/world_bank_mcp_server)

## Примечания

Сервер имеет значок оценки безопасности MseeP.ai и доступен через Smithery для автоматической установки.