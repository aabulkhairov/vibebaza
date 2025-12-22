---
title: TheHive MCP сервер
description: Реализация MCP сервера для платформы реагирования на инциденты безопасности TheHive,
  обеспечивающая стандартизированный доступ к управлению кейсами, обработке алертов, отслеживанию
  наблюдаемых объектов и возможностям интеграции с Cortex.
tags:
- Security
- API
- Integration
- Monitoring
- Analytics
author: redwaysecurity
featured: false
---

Реализация MCP сервера для платформы реагирования на инциденты безопасности TheHive, обеспечивающая стандартизированный доступ к управлению кейсами, обработке алертов, отслеживанию наблюдаемых объектов и возможностям интеграции с Cortex.

## Установка

### UVX

```bash
uvx thehive-mcp-server
```

### Из исходного кода

```bash
pip install .
export HIVE_URL="http://localhost:9000"
export HIVE_API_KEY="your-api-key"
python -m thehive_mcp
```

### UV Run

```bash
uv --directory /path/to/mcp run python -m thehive_mcp.main
```

## Конфигурация

### Claude Desktop (UVX)

```json
{
  "mcpServers": {
    "thehive-mcp-server": {
      "command": "uvx",
      "args": ["thehive-mcp-server"],
      "env": {
        "HIVE_URL": "https://your-thehive-host:9000",
        "HIVE_API_KEY": "your-api-key"
      }
    }
  }
}
```

### Claude Desktop (UV)

```json
{
  "mcpServers": {
    "thehive-mcp-server": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/mcp",
        "run",
        "python",
        "-m",
        "thehive_mcp.main"
      ],
      "env": {
        "HIVE_URL": "https://your-thehive-host:9000",
        "HIVE_API_KEY": "your-api-key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `add_case_attachment` | Добавление вложений к кейсам |
| `assign_task` | Назначение задач пользователям |
| `bulk_delete_alerts` | Удаление нескольких алертов одновременно |
| `bulk_delete_observables` | Удаление нескольких наблюдаемых объектов одновременно |
| `bulk_merge_alerts_into_case` | Объединение нескольких алертов в кейс |
| `bulk_update_alerts` | Обновление нескольких алертов одновременно |
| `bulk_update_cases` | Обновление нескольких кейсов одновременно |
| `bulk_update_observables` | Обновление нескольких наблюдаемых объектов одновременно |
| `bulk_update_tasks` | Обновление нескольких задач одновременно |
| `close_case` | Закрытие кейсов безопасности |
| `complete_task` | Отметка задач как выполненных |
| `count_alerts` | Подсчет алертов в системе |
| `count_cases` | Подсчет кейсов в системе |
| `count_observables` | Подсчет наблюдаемых объектов в системе |
| `count_tasks` | Подсчет задач в системе |

## Возможности

- Комплексное управление кейсами с операциями создания, чтения, обновления и удаления
- Обработка алертов, включая создание, объединение и преобразование в кейсы
- Отслеживание и анализ наблюдаемых объектов с обнаружением схожести
- Управление задачами с назначением, логированием и отслеживанием статуса
- Массовые операции для эффективного управления несколькими элементами
- Интеграция с Cortex для автоматического анализа и реагирования
- Управление файловыми вложениями для кейсов
- Подписка/отписка от алертов для получения уведомлений
- Возможности совместного использования наблюдаемых объектов между инстансами

## Переменные окружения

### Обязательные
- `HIVE_URL` - URL инстанса TheHive (например, https://thehive.company.com:9000)
- `HIVE_API_KEY` - API ключ для аутентификации с инстансом TheHive

## Ресурсы

- [GitHub Repository](https://github.com/redwaysecurity/the-hive-mcp-server)

## Примечания

Этот проект зависит от официальной клиентской библиотеки TheHive (thehive4py), которая будет установлена автоматически. Лицензирован под MIT License.