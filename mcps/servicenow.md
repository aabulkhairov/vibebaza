---
title: ServiceNow MCP сервер
description: MCP сервер, который позволяет Claude подключаться к инстансам ServiceNow,
  получать данные и выполнять действия через ServiceNow API, служащий мостом
  для бесшовной интеграции.
tags:
- CRM
- Integration
- API
- Productivity
- DevOps
author: echelon-ai-labs
featured: true
---

MCP сервер, который позволяет Claude подключаться к инстансам ServiceNow, получать данные и выполнять действия через ServiceNow API, служащий мостом для бесшовной интеграции.

## Установка

### Из исходного кода

```bash
git clone https://github.com/echelon-ai-labs/servicenow-mcp.git
cd servicenow-mcp
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -e .
```

### Стандартный режим (stdio)

```bash
python -m servicenow_mcp.cli
```

### Режим SSE

```bash
servicenow-mcp-sse --instance-url=https://your-instance.service-now.com --username=your-username --password=your-password
```

### MCP CLI

```bash
mcp install src/servicenow_mcp/server.py -f .env
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "ServiceNow": {
      "command": "/Users/yourusername/dev/servicenow-mcp/.venv/bin/python",
      "args": [
        "-m",
        "servicenow_mcp.cli"
      ],
      "env": {
        "SERVICENOW_INSTANCE_URL": "https://your-instance.service-now.com",
        "SERVICENOW_USERNAME": "your-username",
        "SERVICENOW_PASSWORD": "your-password",
        "SERVICENOW_AUTH_TYPE": "basic"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_incident` | Создать новый инцидент в ServiceNow |
| `update_incident` | Обновить существующий инцидент в ServiceNow |
| `add_comment` | Добавить комментарий к инциденту в ServiceNow |
| `resolve_incident` | Закрыть инцидент в ServiceNow |
| `list_incidents` | Получить список инцидентов из ServiceNow |
| `list_catalog_items` | Получить список элементов каталога услуг из ServiceNow |
| `get_catalog_item` | Получить конкретный элемент каталога услуг из ServiceNow |
| `list_catalog_categories` | Получить список категорий каталога услуг из ServiceNow |
| `create_catalog_category` | Создать новую категорию каталога услуг в ServiceNow |
| `update_catalog_category` | Обновить существующую категорию каталога услуг в ServiceNow |
| `move_catalog_items` | Переместить элементы каталога между категориями в ServiceNow |
| `create_catalog_item_variable` | Создать новую переменную (поле формы) для элемента каталога |
| `list_catalog_item_variables` | Получить все переменные для элемента каталога |
| `update_catalog_item_variable` | Обновить существующую переменную для элемента каталога |
| `list_catalogs` | Получить список каталогов услуг из ServiceNow |

## Возможности

- Подключение к инстансам ServiceNow с использованием различных методов аутентификации (Basic, OAuth, API Key)
- Запросы к записям и таблицам ServiceNow
- Создание, обновление и удаление записей ServiceNow
- Выполнение скриптов и воркфлоу ServiceNow
- Доступ к каталогу услуг ServiceNow и запросы к нему
- Анализ и оптимизация каталога услуг ServiceNow
- Режим отладки для устранения неполадок
- Поддержка как stdio, так и Server-Sent Events (SSE) коммуникации
- Упаковка инструментов для управления подмножествами инструментов, доступных языковым моделям
- Ролевые пакеты инструментов для разных типов пользователей (service desk, catalog builder, change coordinator и т.д.)

## Переменные окружения

### Обязательные
- `SERVICENOW_INSTANCE_URL` - URL вашего инстанса ServiceNow
- `SERVICENOW_USERNAME` - Имя пользователя для аутентификации ServiceNow
- `SERVICENOW_PASSWORD` - Пароль для аутентификации ServiceNow
- `SERVICENOW_AUTH_TYPE` - Тип аутентификации (basic, oauth, api_key)

### Опциональные
- `MCP_TOOL_PACKAGE` - Название пакета инструментов для загрузки (контролирует, какие инструменты будут доступны)

## Примеры использования

```
Create a new incident for a network outage in the east region
```

```
Update the priority of incident INC0010001 to high
```

```
Add a comment to incident INC0010001 saying the issue is being investigated
```

```
Resolve incident INC0010001 with a note that the server was restarted
```

```
List all high priority incidents assigned to the Network team
```

## Ресурсы

- [GitHub Repository](https://github.com/osomai/servicenow-mcp)

## Примечания

Сервер поддерживает упаковку инструментов через переменную окружения MCP_TOOL_PACKAGE, позволяя загружать ролевые подмножества инструментов (service_desk, catalog_builder, change_coordinator, knowledge_author, platform_developer, system_administrator, agile_management, full, none). Требуется Python 3.11 или выше.