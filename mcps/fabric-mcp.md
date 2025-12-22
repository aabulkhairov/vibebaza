---
title: Fabric MCP сервер
description: Комплексный Python-based MCP сервер для работы с Microsoft Fabric API, с продвинутыми возможностями разработки, тестирования и оптимизации PySpark ноутбуков с интеграцией LLM.
tags:
- Analytics
- Cloud
- Database
- Code
- AI
author: Community
featured: false
---

Комплексный Python-based MCP сервер для работы с Microsoft Fabric API, с продвинутыми возможностями разработки, тестирования и оптимизации PySpark ноутбуков с интеграцией LLM.

## Установка

### Из исходников

```bash
git clone https://github.com/your-repo/fabric-mcp.git
cd fabric-mcp
uv sync
pip install -r requirements.txt
```

### MCP Inspector

```bash
uv run --with mcp mcp dev fabric_mcp.py
```

### HTTP сервер

```bash
uv run python .\fabric_mcp.py --port 8081
```

## Конфигурация

### VSCode STDIO интеграция

```json
{
    "mcp": {
        "servers": {
            "ms-fabric-mcp": {
                "type": "stdio",
                "command": "<FullPathToProjectFolder>\\.venv\\Scripts\\python.exe",
                "args": ["<FullPathToProjectFolder>\\fabric_mcp.py"]
            }
        }
    }
}
```

### VSCode HTTP интеграция

```json
{
    "mcp": {
        "servers": {
            "ms-fabric-mcp": {
                "type": "http",
                "url": "http://<localhost or remote IP>:8081/mcp/",
                "headers": {
                    "Accept": "application/json,text/event-stream"
                }
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_workspaces` | Показать все доступные Fabric рабочие пространства |
| `set_workspace` | Установить текущий контекст рабочего пространства для сессии |
| `list_lakehouses` | Показать все lakehouse в рабочем пространстве |
| `create_lakehouse` | Создать новый lakehouse |
| `set_lakehouse` | Установить текущий контекст lakehouse |
| `list_warehouses` | Показать все хранилища в рабочем пространстве |
| `create_warehouse` | Создать новое хранилище |
| `set_warehouse` | Установить текущий контекст хранилища |
| `list_tables` | Показать все таблицы в lakehouse |
| `get_lakehouse_table_schema` | Получить схему для конкретной таблицы |
| `get_all_lakehouse_schemas` | Получить схемы для всех таблиц в lakehouse |
| `set_table` | Установить текущий контекст таблицы |
| `get_sql_endpoint` | Получить SQL endpoint для lakehouse или хранилища |
| `run_query` | Выполнить SQL запросы |
| `load_data_from_url` | Загрузить данные из URL в таблицы |

## Возможности

- Управление рабочими пространствами, lakehouse, хранилищами и таблицами
- Получение схем и метаданных Delta таблиц
- Выполнение SQL запросов и загрузка данных
- Операции с отчетами и семантическими моделями
- Интеллектуальное создание ноутбуков с 6 специализированными шаблонами
- Умная генерация кода для типовых PySpark операций
- Комплексная валидация с проверкой синтаксиса и лучших практик
- Fabric-специфичные оптимизации и проверки совместимости
- Анализ производительности с оценкой и рекомендациями по оптимизации
- Мониторинг в реальном времени и аналитика выполнения

## Примеры использования

```
List all my Fabric workspaces
```

```
Create a PySpark notebook that reads sales data, cleans it, and optimizes performance
```

```
My PySpark notebook is slow. Help me optimize it.
```

## Ресурсы

- [GitHub Repository](https://github.com/aci-labs/ms-fabric-mcp)

## Примечания

Требует Azure аутентификацию (az login --scope https://api.fabric.microsoft.com/.default). Включает 6 специализированных PySpark шаблонов: basic, etl, analytics, ml, fabric_integration и streaming. Предоставляет оценку производительности (0-100) и детальные рекомендации по оптимизации. Поддерживает как STDIO, так и HTTP режимы коммуникации.