---
title: kill-process-mcp сервер
description: Кроссплатформенный MCP сервер, который предоставляет инструменты для просмотра и завершения системных процессов через естественные языковые запросы, идеален для остановки ресурсоемких процессов.
tags:
- Monitoring
- DevOps
- Productivity
- Security
author: misiektoja
featured: false
---

Кроссплатформенный MCP сервер, который предоставляет инструменты для просмотра и завершения системных процессов через естественные языковые запросы, идеален для остановки ресурсоемких процессов.

## Установка

### UVX (Рекомендуется)

```bash
pip install uv
# или на macOS:
brew install uv
```

### Из исходного кода

```bash
git clone https://github.com/misiektoja/kill-process-mcp.git
cd kill-process-mcp
uv sync
```

### Постоянная установка

```bash
uv tool install kill-process-mcp
```

## Конфигурация

### Claude Desktop (UVX)

```json
{
    "mcpServers": {
        "kill-process-mcp": {
            "command": "uvx",
            "args": ["kill-process-mcp@latest"]
        }
    }
}
```

### Claude Desktop (Ручная)

```json
{
    "mcpServers": {
        "kill-process-mcp": {
            "command": "uv",
            "args": [
                "run",
                "--directory",
                "/path/to/kill-process-mcp",
                "kill_process_mcp.py"
            ]
        }
    }
}
```

### Cursor (UVX)

```json
{
    "mcpServers": {
        "kill-process-mcp": {
            "command": "uvx",
            "args": ["kill-process-mcp@latest"]
        }
    }
}
```

### Cursor (Ручная)

```json
{
    "mcpServers": {
        "kill-process-mcp": {
            "command": "uv",
            "args": [
                "run",
                "--directory",
                "/path/to/kill-process-mcp",
                "kill_process_mcp.py"
            ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `process_list` | Отображает запущенные процессы, отсортированные по CPU или памяти с опциональной фильтрацией по имени, пользователю, статусу, порогам CPU/памяти... |
| `process_kill` | Завершает выбранный процесс (безжалостно!) |

## Возможности

- Кроссплатформенная поддержка (macOS/Windows/Linux)
- Список процессов с фильтрацией по имени, пользователю, статусу, порогам CPU/памяти
- Сортировка процессов по использованию CPU или памяти
- Завершение процессов по выбору
- Интерфейс естественных языковых запросов
- Фильтрация системных и пользовательских процессов

## Примеры использования

```
Kill the damn process slowing down my system!
```

```
Check my top 5 CPU parasites and flag any that look like malware
```

```
List the 3 greediest processes by RAM usage
```

```
Exterminate every process with Spotify in its name
```

```
List Alice's Python processes, max 10 entries
```

## Ресурсы

- [GitHub Repository](https://github.com/misiektoja/kill-process-mcp)

## Примечания

Требует Python 3.13 или выше и менеджер пакетов uv. Сервер поставляется с юмористическим предупреждением о том, что он "вооружен и опасен" - пользователи должны проявлять осторожность при завершении процессов. Метод UVX автоматически загружает последнюю версию при каждом запуске.