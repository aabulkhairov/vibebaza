---
title: CFBD API MCP сервер
description: Реализация MCP сервера, предоставляющая доступ к статистике студенческого футбола через College Football Data API V2. Позволяет запрашивать результаты игр, записи команд, статистику игроков, данные по ходу игры и рейтинги.
tags:
- API
- Analytics
- Database
- Integration
author: lenwood
featured: false
install_command: npx -y @smithery/cli install cfbd --client claude
---

Реализация MCP сервера, предоставляющая доступ к статистике студенческого футбола через College Football Data API V2. Позволяет запрашивать результаты игр, записи команд, статистику игроков, данные по ходу игры и рейтинги.

## Установка

### Smithery

```bash
npx -y @smithery/cli install cfbd --client claude
```

### Из исходников

```bash
git clone https://github.com/yourusername/cfbd-mcp-server
cd cfbd-mcp-server
uv venv
source .venv/bin/activate
uv pip install -e .
```

### Запуск сервера

```bash
uv run cfbd-mcp-server
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "cfbd-mcp-server": {
            "command": "uv",
            "args": [
                "--directory",
                "/full/path/to/cfbd-mcp-server",
                "run",
                "cfbd-mcp-server"
            ],
            "env": {
                "CFB_API_KEY": "xxx",
                "PATH": "/full/path/to/python"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-games` | Получение данных об играх |
| `get-records` | Получение записей команд |
| `get-games-teams` | Доступ к статистике командных игр |
| `get-plays` | Запрос данных по ходу игры |
| `get-drives` | Анализ информации о драйвах |
| `get-play-stats` | Просмотр статистики розыгрышей |
| `get-rankings` | Проверка рейтингов команд |
| `get-pregame-win-probability` | Просмотр вероятностей побед |
| `get-advanced-box-score` | Доступ к детальной статистике и аналитике игр |

## Возможности

- Запрос всеобъемлющей статистики и данных студенческого футбола
- Доступ к результатам игр, записям команд и статистике игроков
- Анализ данных по ходу игры и сводок драйвов
- Просмотр рейтингов и метрик вероятности побед
- Сравнение выступлений команд и генерация инсайтов
- Готовые шаблоны анализа для игр, команд, трендов и соперничества
- Поддержка запросов на естественном языке

## Переменные окружения

### Обязательные
- `CFB_API_KEY` - ключ College Football Data API

## Примеры использования

```
What was the largest upset among FCS games during the 2014 season?
```

```
Analyze game performance between two specific teams
```

```
Compare team performances across seasons
```

```
Analyze historical rivalry matchups
```

```
Get detailed analysis of a specific game
```

## Ресурсы

- [GitHub Repository](https://github.com/lenwood/cfbd-mcp-server)

## Примечания

Требует Python 3.11+ и менеджер пакетов UV. College Football Data API имеет ограничения по частоте запросов - бесплатный тариф ограничивает количество запросов в минуту, подписчики Patreon получают более высокие лимиты. Включает всеобъемлющую документацию схемы и готовые промпты для анализа.