---
title: Fabric Real-Time Intelligence MCP сервер
description: Комплексный MCP сервер для Microsoft Fabric Real-Time Intelligence (RTI), который позволяет AI агентам взаимодействовать с Eventhouse/Azure Data Explorer, Eventstreams и сервисами Activator через естественные языковые запросы и KQL операции.
tags:
- Analytics
- Database
- Cloud
- Messaging
- Monitoring
author: Community
featured: false
---

Комплексный MCP сервер для Microsoft Fabric Real-Time Intelligence (RTI), который позволяет AI агентам взаимодействовать с Eventhouse/Azure Data Explorer, Eventstreams и сервисами Activator через естественные языковые запросы и KQL операции.

## Установка

### PyPI с UVX

```bash
uvx microsoft-fabric-rti-mcp
```

### Сначала установите UV

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Из исходного кода

```bash
pip install .
```

### Локальная разработка

```bash
pip install -e ".[dev]"
```

## Конфигурация

### VS Code settings.json

```json
{
    "mcp": {
        "server": {
            "fabric-rti-mcp": {
                "command": "uvx",
                "args": [
                    "microsoft-fabric-rti-mcp"
                ],
                "env": {
                    "KUSTO_SERVICE_URI": "https://help.kusto.windows.net/",
                    "KUSTO_SERVICE_DEFAULT_DB": "Samples",
                    "FABRIC_API_BASE_URL": "https://api.fabric.microsoft.com/v1"
                }
            }
        }
    }
}
```

### Конфигурация для ручной установки

```json
{
    "mcp": {
        "servers": {
            "fabric-rti-mcp": {
                "command": "uv",
                "args": [
                    "--directory",
                    "C:/path/to/fabric-rti-mcp/",
                    "run",
                    "-m",
                    "fabric_rti_mcp.server"
                ],
                "env": {
                    "KUSTO_SERVICE_URI": "https://help.kusto.windows.net/",
                    "KUSTO_SERVICE_DEFAULT_DB": "Samples",
                    "FABRIC_API_BASE_URL": "https://api.fabric.microsoft.com/v1"
                }
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `kusto_known_services` | Список всех доступных сервисов Kusto, настроенных в MCP |
| `kusto_query` | Выполнение KQL запросов к указанной базе данных |
| `kusto_command` | Выполнение управляющих команд Kusto (деструктивные операции) |
| `kusto_list_databases` | Список всех баз данных в кластере Kusto |
| `kusto_list_tables` | Список всех таблиц в указанной базе данных |
| `kusto_get_entities_schema` | Получение информации о схеме для всех сущностей (таблицы, материализованные представления, функции) в базе данных |
| `kusto_get_table_schema` | Получение подробной информации о схеме для конкретной таблицы |
| `kusto_get_function_schema` | Получение информации о схеме для конкретной функции, включая параметры и схему вывода |
| `kusto_sample_table_data` | Извлечение случайных образцов записей из указанной таблицы |
| `kusto_sample_function_data` | Извлечение случайных образцов записей из результата вызова функции |
| `kusto_ingest_inline_into_table` | Загрузка встроенных CSV данных в указанную таблицу |
| `kusto_get_shots` | Извлечение семантически похожих примеров запросов из таблицы shots с использованием AI embeddings |
| `eventstream_list` | Список всех Eventstreams в вашем рабочем пространстве Fabric |
| `eventstream_get` | Получение подробной информации о конкретном Eventstream |
| `eventstream_get_definition` | Извлечение полного JSON определения Eventstream |

## Возможности

- Перевод естественного языка в KQL запросы
- Безопасная аутентификация через Azure Identity
- Доступ к данным в реальном времени из Eventhouse и Eventstreams
- Выполнение KQL запросов к Microsoft Fabric RTI Eventhouse и Azure Data Explorer
- Управление Eventstreams для обработки данных в реальном времени
- Создание и управление триггерами Activator для оповещений в реальном времени
- Функциональность семантического поиска с AI embeddings
- Возможности встроенной загрузки данных
- Обнаружение схем и выборка таблиц
- Поддержка уведомлений по электронной почте и Teams

## Переменные окружения

### Опциональные
- `KUSTO_SERVICE_URI` - URI кластера Kusto по умолчанию
- `KUSTO_SERVICE_DEFAULT_DB` - Имя базы данных по умолчанию для Kusto запросов
- `AZ_OPENAI_EMBEDDING_ENDPOINT` - Конечная точка Azure OpenAI embedding для семантического поиска в kusto_get_shots
- `KUSTO_KNOWN_SERVICES` - JSON массив предварительно настроенных сервисов Kusto
- `KUSTO_EAGER_CONNECT` - Следует ли активно подключаться к сервису по умолчанию при запуске
- `KUSTO_ALLOW_UNKNOWN_SERVICES` - Настройка безопасности для разрешения подключений к сервисам, не входящим в KUSTO_KNOWN_SERVICES
- `FABRIC_API_BASE` - Базовый URL для Microsoft Fabric API
- `FABRIC_BASE_URL` - Базовый URL для веб-интерфейса Microsoft Fabric

## Примеры использования

```
Get databases in my Eventhouse
```

```
Sample 10 rows from table 'StormEvents' in Eventhouse
```

```
What can you tell me about StormEvents data?
```

```
Analyze the StormEvents to come up with trend analysis across past 10 years of data
```

```
Analyze the commands in 'CommandExecution' table and categorize them as low/medium/high risks
```

## Ресурсы

- [GitHub Repository](https://github.com/Microsoft/fabric-rti-mcp)

## Примечания

Этот проект находится в публичном превью, и реализация может значительно измениться до общего релиза. Сервер поддерживает как Eventhouse (Kusto) с 12 инструментами, Eventstreams с 17 инструментами, так и Activator с 2 инструментами. Требует Python 3.10+ и бесшовно интегрируется с VS Code через GitHub Copilot.