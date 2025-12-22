---
title: Fantasy PL MCP сервер
description: Сервер Model Context Protocol (MCP), который предоставляет доступ к данным и инструментам Fantasy Premier League (FPL), позволяя взаимодействовать с подробной статистикой игроков, информацией о командах и данными игровых недель в Claude Desktop и других MCP-совместимых клиентах.
tags:
- API
- Analytics
- Database
- Integration
- Productivity
author: Community
featured: false
---

Сервер Model Context Protocol (MCP), который предоставляет доступ к данным и инструментам Fantasy Premier League (FPL), позволяя взаимодействовать с подробной статистикой игроков, информацией о командах и данными игровых недель в Claude Desktop и других MCP-совместимых клиентах.

## Установка

### PyPI (Рекомендуется)

```bash
pip install fpl-mcp
```

### PyPI с зависимостями для разработки

```bash
pip install "fpl-mcp[dev]"
```

### Из GitHub

```bash
pip install git+https://github.com/rishijatia/fantasy-pl-mcp.git
```

### Клонирование и локальная установка

```bash
git clone https://github.com/rishijatia/fantasy-pl-mcp.git
cd fantasy-pl-mcp
pip install -e .
```

### CLI команда

```bash
fpl-mcp
```

## Конфигурация

### Claude Desktop (Python модуль)

```json
{
  "mcpServers": {
    "fantasy-pl": {
      "command": "python",
      "args": ["-m", "fpl_mcp"]
    }
  }
}
```

### Claude Desktop (полный путь)

```json
{
  "mcpServers": {
    "fantasy-pl": {
      "command": "/full/path/to/your/venv/bin/fpl-mcp"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|-----------|
| `get_gameweek_status` | Получить точную информацию о текущих, предыдущих и следующих игровых неделях |
| `analyze_player_fixtures` | Анализ предстоящих матчей для игрока с рейтингами сложности |
| `get_blank_gameweeks` | Получить информацию о предстоящих пустых игровых неделях |
| `get_double_gameweeks` | Получить информацию о предстоящих удвоенных игровых неделях |
| `analyze_players` | Фильтровать и анализировать игроков FPL по множественным критериям |
| `analyze_fixtures` | Анализ предстоящих матчей для игроков, команд или позиций |
| `compare_players` | Сравнить нескольких игроков по различным метрикам |
| `check_fpl_authentication` | Проверить, правильно ли работает аутентификация FPL |
| `get_my_team` | Просмотр вашей авторизованной команды (требует аутентификацию) |
| `get_team` | Просмотр любой команды с определенным ID (требует аутентификацию) |
| `get_manager_info` | Получить детали менеджера (требует аутентификацию) |

## Возможности

- Богатые данные игроков: Доступ к подробной статистике игроков из FPL API
- Информация о командах: Получение деталей о командах Premier League
- Данные игровых недель: Просмотр текущей и прошлых игровых недель
- Поиск игроков: Найти игроков по имени или команде
- Сравнение игроков: Сравнить подробную статистику между любыми двумя игроками

## Переменные окружения

### Опциональные
- `FPL_EMAIL` - Ваш email Fantasy Premier League для аутентификации
- `FPL_PASSWORD` - Ваш пароль Fantasy Premier League для аутентификации
- `FPL_TEAM_ID` - ID вашей команды Fantasy Premier League для аутентификации

## Примеры использования

```
Compare Mohamed Salah and Erling Haaland over the last 5 gameweeks
```

```
Find all Arsenal midfielders
```

```
What's the current gameweek status?
```

```
Show me the top 5 forwards by points
```

```
Show upcoming fixtures for [Team]
```

## Ресурсы

- [GitHub Repository](https://github.com/rishijatia/fantasy-pl-mcp)

## Примечания

Поддерживает Claude Desktop, Cursor, Windsurf и другие MCP-совместимые десктопные LLM. Мобильные версии в настоящее время не поддерживаются. Требует Python 3.10 или выше. Аутентификация опциональна, но необходима для функций вроде доступа к вашей команде. FPL API официально не документирован и может изменяться без предупреждения.