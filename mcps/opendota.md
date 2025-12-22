---
title: OpenDota MCP сервер
description: Реализация сервера Model Context Protocol (MCP) для доступа к данным OpenDota API, позволяющая LLM и AI-ассистентам получать статистику Dota 2 в реальном времени, данные матчей, информацию об игроках и многое другое через стандартный интерфейс.
tags:
- API
- Analytics
- Integration
author: asusevski
featured: false
install_command: npx -y @smithery/cli install @asusevski/opendota-mcp-server --client
  claude
---

Реализация сервера Model Context Protocol (MCP) для доступа к данным OpenDota API, позволяющая LLM и AI-ассистентам получать статистику Dota 2 в реальном времени, данные матчей, информацию об игроках и многое другое через стандартный интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @asusevski/opendota-mcp-server --client claude
```

### Из исходного кода

```bash
git clone https://github.com/asusevski/opendota-mcp-server.git
cd opendota-mcp-server

# Вариант 1: Автоматическая настройка
./scripts/setup_env.sh

# Вариант 2: Ручная установка с uv
uv add pyproject.toml

# Для зависимостей разработки
uv pip install -e ".[dev]"
```

### Прямой запуск

```bash
python -m src.opendota_server.server
```

## Конфигурация

### Claude Desktop (WSL)

```json
{
  "mcpServers": {
    "opendota": {
      "command": "wsl.exe",
      "args": [
        "--",
        "bash",
        "-c",
        "cd ~/opendota-mcp-server && source .venv/bin/activate && python src/opendota_server/server.py"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_player_by_id` | Получить информацию об игроке по ID аккаунта |
| `get_player_recent_matches` | Получить недавние матчи игрока |
| `get_match_data` | Получить подробные данные конкретного матча |
| `get_player_win_loss` | Получить статистику побед/поражений игрока |
| `get_player_heroes` | Получить наиболее играемых героев игрока |
| `get_hero_stats` | Получить статистику героев |
| `search_player` | Найти игроков по имени |
| `get_pro_players` | Получить список профессиональных игроков |
| `get_pro_matches` | Получить недавние профессиональные матчи |
| `get_player_peers` | Получить игроков, которые играли с указанным игроком |
| `get_heroes` | Получить список всех героев Dota 2 |
| `get_player_totals` | Получить общую статистику игрока |
| `get_player_rankings` | Получить рейтинги героев игрока |
| `get_player_wordcloud` | Получить наиболее часто используемые слова игрока в чате |
| `get_team_info` | Получить информацию о команде |

## Возможности

- Доступ к профилям игроков, статистике и истории матчей
- Получение детальной информации о матчах
- Поиск профессиональных игроков и команд
- Получение статистики и рейтингов героев
- Поиск игроков по имени

## Переменные окружения

### Опциональные
- `OPENDOTA_API_KEY` - API ключ OpenDota для доступа к API (получить на https://www.opendota.com/api-keys)

## Ресурсы

- [GitHub Repository](https://github.com/asusevski/opendota-mcp-server)

## Примечания

Рекомендуется, но не обязательно создать API ключ OpenDota на https://www.opendota.com/api-keys. Включает значок оценки безопасности от MseeP.ai. Лицензируется под MIT.