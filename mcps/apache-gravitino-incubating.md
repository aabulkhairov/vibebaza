---
title: Apache Gravitino(incubating) MCP сервер
description: MCP сервер с Gravitino API для исследования метаданных структурированных
  и неструктурированных данных, с поддержкой задач data governance — тегирование,
  классификация и управление ролями пользователей.
tags:
- Database
- Analytics
- API
- Integration
- Security
author: datastrato
featured: false
---

MCP сервер с Gravitino API для исследования метаданных структурированных и неструктурированных данных, с поддержкой задач data governance — тегирование, классификация и управление ролями пользователей.

## Установка

### Из исходников с UV

```bash
git clone git@github.com:datastrato/mcp-server-gravitino.git
cd mcp-server-gravitino
uv venv
source .venv/bin/activate
uv install
```

## Конфигурация

### Goose Client

```json
{
  "mcpServers": {
    "Gravitino": {
      "command": "uv",
      "args": [
        "--directory",
        "/Users/user/workspace/mcp-server-gravitino",
        "run",
        "--with",
        "fastmcp",
        "--with",
        "httpx",
        "--with",
        "mcp-server-gravitino",
        "python",
        "-m",
        "mcp_server_gravitino.server"
      ],
      "env": {
        "GRAVITINO_URI": "http://localhost:8090",
        "GRAVITINO_USERNAME": "admin",
        "GRAVITINO_PASSWORD": "admin",
        "GRAVITINO_METALAKE": "metalake_demo"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_list_of_catalogs` | Получить список каталогов |
| `get_list_of_schemas` | Получить список схем |
| `get_list_of_tables` | Получить пагинированный список таблиц |
| `get_table_by_fqn` | Получить детальную информацию о конкретной таблице |
| `get_table_columns_by_fqn` | Получить информацию о колонках таблицы |
| `get_list_of_tags` | Получить все теги |
| `associate_tag_to_entity` | Прикрепить тег к таблице или колонке |
| `list_objects_by_tag` | Список объектов, связанных с конкретным тегом |
| `get_list_of_roles` | Получить все роли |
| `get_list_of_users` | Получить всех пользователей |
| `grant_role_to_user` | Назначить роль пользователю |
| `revoke_role_from_user` | Отозвать роль у пользователя |
| `get_list_of_models` | Получить список моделей |
| `get_list_of_model_versions_by_fqn` | Получить версии модели по полному квалифицированному имени |

## Возможности

- Бесшовная интеграция с FastMCP для Gravitino API
- Упрощённый интерфейс для взаимодействия с метаданными
- Поддержка операций с метаданными для каталогов, схем, таблиц, моделей, пользователей, тегов и управления ролями
- Токен-based и basic методы аутентификации
- Выборочная активация инструментов по именам методов
- Оптимизированные инструменты для соблюдения лимитов токенов LLM с сохранением семантической целостности

## Переменные окружения

### Обязательные
- `GRAVITINO_URI` — базовый URL вашего сервера Gravitino

### Опциональные
- `GRAVITINO_METALAKE` — имя metalake для использования (по умолчанию: 'metalake_demo')
- `GRAVITINO_JWT_TOKEN` — JWT токен для аутентификации
- `GRAVITINO_USERNAME` — имя пользователя для аутентификации Gravitino
- `GRAVITINO_PASSWORD` — соответствующий пароль для basic аутентификации
- `GRAVITINO_ACTIVE_TOOLS` — указать какие инструменты активировать (по умолчанию: '*' для всех)

## Ресурсы

- [GitHub Repository](https://github.com/datastrato/mcp-server-gravitino)

## Примечания

Требуется Python 3.10+ и использует UV для управления зависимостями. Поддерживает JWT токен и basic аутентификацию. Активация инструментов может быть настроена для включения только определённой функциональности. Сервер разработан для работы с интеграцией FastMCP и возвращает компактные метаданные для оптимизации использования LLM.
