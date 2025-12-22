---
title: SoccerDataAPI MCP сервер
description: MCP сервер, который подключается к SoccerDataAPI для получения информации о футбольных матчах в реальном времени, включая текущие счета, составы, события и коэффициенты букмекеров через естественные языковые запросы.
tags:
- API
- Analytics
- Integration
- Search
author: Community
featured: false
---

MCP сервер, который подключается к SoccerDataAPI для получения информации о футбольных матчах в реальном времени, включая текущие счета, составы, события и коэффициенты букмекеров через естественные языковые запросы.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @yeonupark/mcp-soccer-data --client claude
```

### Из исходного кода

```bash
git clone https://github.com/yeonupark/mcp-soccer-data.git
cd mcp-soccer-data
uv sync
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
      "mcp-soccer-data": {
          "command": "/ABSOLUTE/PATH/TO/PARENT/FOLDER/uv",
          "args": [
              "--directory",
              "/ABSOLUTE/PATH/TO/PARENT/FOLDER/src/",
              "run",
              "--env-file",
              "/ABSOLUTE/PATH/TO/PARENT/FOLDER/.env",
              "server.py"
          ]
      }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_livescores` | Возвращает информацию в реальном времени о текущих футбольных матчах по всему миру |

## Возможности

- Информация о живых футбольных матчах с данными в реальном времени
- Списки матчей с базовой информацией (команды, время начала, стадион, текущий счет)
- Подробная информация о матчах (статус, разбивка голов, итоговый результат)
- Ключевые события матчей (голы, замены, карточки, пенальти)
- Составы команд (основной состав, запасные игроки, статус травм, расстановка)
- Информация о коэффициентах и ставках (победа/ничья/поражение, больше/меньше, фора)
- Метаданные лиг (название, страна, формат соревнований)
- Фокус на живых, предстоящих и недавно завершившихся матчах

## Переменные окружения

### Обязательные
- `AUTH_KEY` - Ключ аутентификации с soccerdataapi.com

## Примеры использования

```
What football matches are being played right now?
```

```
What are the predicted lineups for PSG vs Aston Villa today?
```

```
Please tell me the scores and number of goals from recent football matches.
```

## Ресурсы

- [GitHub Repository](https://github.com/yeonupark/mcp-soccer-data)

## Примечания

Требует Python 3.12+, менеджер пакетов uv и аккаунт Soccerdata API с https://soccerdataapi.com/. Сервер сфокусирован исключительно на живых, предстоящих и недавно завершившихся матчах.