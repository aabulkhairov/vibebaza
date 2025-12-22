---
title: Fleet MCP сервер
description: MCP сервер, который позволяет AI-ассистентам взаимодействовать с Fleet Device Management для управления устройствами, мониторинга безопасности и обеспечения соответствия требованиям.
tags:
- Security
- DevOps
- Monitoring
- Integration
- API
author: SimplyMinimal
featured: false
---

MCP сервер, который позволяет AI-ассистентам взаимодействовать с Fleet Device Management для управления устройствами, мониторинга безопасности и обеспечения соответствия требованиям.

## Установка

### UVX (Рекомендуется)

```bash
uvx fleet-mcp run
```

### PyPI

```bash
pip install fleet-mcp
```

### Из исходного кода

```bash
git clone https://github.com/SimplyMinimal/fleet-mcp.git
cd fleet-mcp
pip install -e .
```

### Разработка с UV

```bash
git clone https://github.com/SimplyMinimal/fleet-mcp.git
cd fleet-mcp
uv sync --dev
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "fleet": {
      "command": "uvx",
      "args": ["fleet-mcp", "run"],
      "env": {
        "FLEET_SERVER_URL": "https://your-fleet-instance.com",
        "FLEET_API_TOKEN": "your-api-token",
        "FLEET_READONLY": "true",
        "FLEET_ALLOW_SELECT_QUERIES": "true"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "fleet": {
      "command": "uvx",
      "args": ["fleet-mcp", "run"],
      "env": {
        "FLEET_SERVER_URL": "https://your-fleet-instance.com",
        "FLEET_API_TOKEN": "your-api-token",
        "FLEET_READONLY": "true",
        "FLEET_ALLOW_SELECT_QUERIES": "true"
      }
    }
  }
}
```

### Cline (VS Code)

```json
{
  "mcpServers": {
    "fleet": {
      "command": "uvx",
      "args": ["fleet-mcp", "run"],
      "env": {
        "FLEET_SERVER_URL": "https://your-fleet-instance.com",
        "FLEET_API_TOKEN": "your-api-token",
        "FLEET_READONLY": "true",
        "FLEET_ALLOW_SELECT_QUERIES": "true"
      }
    }
  }
}
```

### Zed Editor

```json
{
  "context_servers": {
    "fleet": {
      "command": {
        "path": "uvx",
        "args": ["fleet-mcp", "run"]
      },
      "settings": {
        "env": {
          "FLEET_SERVER_URL": "https://your-fleet-instance.com",
          "FLEET_API_TOKEN": "your-api-token",
          "FLEET_READONLY": "true",
          "FLEET_ALLOW_SELECT_QUERIES": "true"
        }
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `fleet_list_hosts` | Список хостов с фильтрацией, пагинацией и поиском |
| `fleet_get_host` | Получить подробную информацию о конкретном хосте по ID |
| `fleet_get_host_by_identifier` | Получить хост по имени хоста, UUID или серийному номеру |
| `fleet_search_hosts` | Поиск хостов по имени, UUID, серийному номеру или IP |
| `fleet_list_queries` | Список всех сохранённых запросов с пагинацией |
| `fleet_get_query` | Получить детали конкретного сохранённого запроса |
| `fleet_get_query_report` | Получить последние результаты запланированного запроса |
| `fleet_list_policies` | Список всех политик соответствия |
| `fleet_get_policy_results` | Получить результаты соответствия для конкретной политики |
| `fleet_list_software` | Список инвентаря программного обеспечения по всему парку |
| `fleet_get_vulnerabilities` | Список известных уязвимостей с фильтрацией |
| `fleet_get_cve` | Получить подробную информацию о конкретном CVE |
| `fleet_list_teams` | Список всех команд |
| `fleet_list_users` | Список всех пользователей с фильтрацией |
| `fleet_list_labels` | Список всех меток |

## Возможности

- Управление хостами - просмотр, поиск, запросы и управление хостами в вашем парке
- Выполнение запросов в реальном времени - выполнение osquery запросов в реальном времени на хостах
- Управление политиками - создание, обновление и мониторинг политик соответствия
- Инвентарь программного обеспечения - отслеживание установленного ПО и уязвимостей на устройствах
- Управление командами и пользователями - организация хостов и пользователей в команды
- Обнаружение таблиц osquery - динамическое обнаружение и документирование таблиц osquery
- Режим только для чтения - безопасное исследование с дополнительным выполнением только SELECT запросов
- Мониторинг активности - отслеживание активности Fleet и журналов аудита

## Переменные окружения

### Обязательные
- `FLEET_SERVER_URL` - URL сервера Fleet
- `FLEET_API_TOKEN` - API токен Fleet

### Опциональные
- `FLEET_READONLY` - Включить режим только для чтения
- `FLEET_ALLOW_SELECT_QUERIES` - Разрешить SELECT запросы в режиме только для чтения
- `FLEET_VERIFY_SSL` - Проверка SSL сертификатов
- `FLEET_TIMEOUT` - Таймаут запроса (секунды)
- `FLEET_MAX_RETRIES` - Максимальное количество повторных попыток

## Примеры использования

```
Покажи мне все хосты в моём парке
```

```
Какие политики сейчас не соответствуют требованиям?
```

```
Выполни запрос в реальном времени для проверки конкретного ПО
```

```
Покажи все уязвимости, найденные в парке
```

```
Покажи инвентарь ПО для конкретного хоста
```

## Ресурсы

- [GitHub Repository](https://github.com/SimplyMinimal/fleet-mcp)

## Примечания

Поддерживает как режим только для чтения, так и режим чтения-записи. Режим только для чтения является безопасным по умолчанию для исследования. API токен можно сгенерировать в интерфейсе Fleet (Мой аккаунт → Получить API токен) или через команду fleetctl. Улучшенные практики безопасности включают использование TOML конфигурационных файлов и правильных разрешений файлов.