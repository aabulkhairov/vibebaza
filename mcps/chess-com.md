---
title: Chess.com MCP сервер
description: MCP сервер для Published Data API Chess.com, который предоставляет доступ к данным игроков Chess.com, записям игр и другой публичной информации через стандартизированные MCP интерфейсы для AI-ассистентов.
tags:
- API
- Analytics
- Search
- Productivity
- Integration
author: pab1it0
featured: false
---

MCP сервер для Published Data API Chess.com, который предоставляет доступ к данным игроков Chess.com, записям игр и другой публичной информации через стандартизированные MCP интерфейсы для AI-ассистентов.

## Установка

### Docker

```bash
docker run --rm -i pab1it0/chess-mcp
```

### UV

```bash
uv --directory <full path to chess-mcp directory> run src/chess_mcp/main.py
```

### Из исходного кода

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv venv
source .venv/bin/activate  # На Unix/macOS
.venv\Scripts\activate     # На Windows
uv pip install -e .
```

## Конфигурация

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "chess": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "pab1it0/chess-mcp"
      ]
    }
  }
}
```

### Claude Desktop (UV)

```json
{
  "mcpServers": {
    "chess": {
      "command": "uv",
      "args": [
        "--directory",
        "<full path to chess-mcp directory>",
        "run",
        "src/chess_mcp/main.py"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_player_profile` | Получить профиль игрока с Chess.com |
| `get_player_stats` | Получить статистику игрока с Chess.com |
| `is_player_online` | Проверить, находится ли игрок в сети на Chess.com |
| `get_titled_players` | Получить список титулованных игроков с Chess.com |
| `get_player_current_games` | Получить текущие игры игрока на Chess.com |
| `get_player_games_by_month` | Получить игры игрока за определенный месяц с Chess.com |
| `get_player_game_archives` | Получить список доступных месячных архивов игр для игрока на Chess.com |
| `download_player_games_pgn` | Скачать PGN файлы всех игр за определенный месяц с Chess.com |
| `get_club_profile` | Получить информацию о клубе на Chess.com |
| `get_club_members` | Получить участников клуба на Chess.com |

## Возможности

- Доступ к профилям игроков, статистике и записям игр
- Поиск игр по дате и игроку
- Проверка онлайн-статуса игрока
- Получение информации о клубах и титулованных игроках
- Не требует аутентификации (использует публичный API Chess.com)
- Поддержка контейнеризации Docker
- Предоставляет интерактивные инструменты для AI-ассистентов
- Настраиваемый список инструментов

## Ресурсы

- [GitHub Repository](https://github.com/pab1it0/chess-mcp)

## Примечания

Список инструментов настраивается, так что вы можете выбрать, какие инструменты хотите сделать доступными для MCP клиента. Если вы видите ошибку 'Error: spawn uv ENOENT' в Claude Desktop, возможно, нужно указать полный путь к uv или установить переменную окружения NO_UV=1 в конфигурации.