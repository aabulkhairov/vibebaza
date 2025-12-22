---
title: TFT-Match-Analyzer MCP сервер
description: Model Context Protocol (MCP) сервер для Team Fight Tactics (TFT), который предоставляет доступ к игровым данным TFT, включая историю матчей и детальную информацию о матчах.
tags:
- API
- Analytics
- Integration
author: GeLi2001
featured: false
---

Model Context Protocol (MCP) сервер для Team Fight Tactics (TFT), который предоставляет доступ к игровым данным TFT, включая историю матчей и детальную информацию о матчах.

## Установка

### NPX

```bash
npx mcp-server-tft --apiKey <YOUR_RIOT_API_KEY> --gameName <YOUR_GAME_NAME> --tagLine <YOUR_TAG_LINE>
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "tft-mcp": {
      "command": "npx",
      "args": [
        "mcp-server-tft",
        "--apiKey",
        "<YOUR_RIOT_API_KEY>",
        "--gameName",
        "<YOUR_GAME_NAME>",
        "--tagLine",
        "<YOUR_TAG_LINE>"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `tft_match_history` | Получить историю TFT матчей для текущего игрока с опциональными параметрами count и start для пагинации |
| `tft_match_details` | Получить детальную информацию о конкретном TFT матче, используя ID матча |

## Возможности

- Получение истории матчей для призывателя
- Получение детальной информации о конкретных TFT матчах

## Ресурсы

- [GitHub Repository](https://github.com/GeLi2001/tft-mcp-server)

## Примечания

Требуется API ключ от Riot Games с developer.riotgames.com (временный 24-часовой ключ для разработки, постоянный персональный API ключ для продакшена). Также требуются ваше игровое имя и тег из консоли игры Riot. Построен с использованием TypeScript и Model Context Protocol SDK.