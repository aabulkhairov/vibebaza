---
title: Azure ADX MCP сервер
description: MCP сервер, который позволяет AI-ассистентам выполнять KQL запросы и исследовать базы данных Azure Data Explorer (ADX/Kusto) через стандартизированные интерфейсы, с поддержкой как автономных ADX кластеров, так и Microsoft Fabric Eventhouse кластеров.
tags:
- Database
- Analytics
- Cloud
- Integration
- DevOps
author: pab1it0
featured: false
---

MCP сервер, который позволяет AI-ассистентам выполнять KQL запросы и исследовать базы данных Azure Data Explorer (ADX/Kusto) через стандартизированные интерфейсы, с поддержкой как автономных ADX кластеров, так и Microsoft Fabric Eventhouse кластеров.

## Установка

### Из исходного кода с uv

```bash
uv --directory <full path to adx-mcp-server directory> run src/adx_mcp_server/main.py
```

### Сборка Docker

```bash
docker build -t adx-mcp-server .
```

### Запуск Docker

```bash
docker run -it --rm \
  -e ADX_CLUSTER_URL=https://yourcluster.region.kusto.windows.net \
  -e ADX_DATABASE=your_database \
  -e AZURE_TENANT_ID=your_tenant_id \
  -e AZURE_CLIENT_ID=your_client_id \
  adx-mcp-server
```

### Docker Compose

```bash
docker-compose up
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "adx": {
      "command": "uv",
      "args": [
        "--directory",
        "<full path to adx-mcp-server directory>",
        "run",
        "src/adx_mcp_server/main.py"
      ],
      "env": {
        "ADX_CLUSTER_URL": "https://yourcluster.region.kusto.windows.net",
        "ADX_DATABASE": "your_database"
      }
    }
  }
}
```

### Claude Desktop с Docker

```json
{
  "mcpServers": {
    "adx": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "-e", "ADX_CLUSTER_URL",
        "-e", "ADX_DATABASE",
        "-e", "AZURE_TENANT_ID",
        "-e", "AZURE_CLIENT_ID",
        "-e", "ADX_TOKEN_FILE_PATH",
        "adx-mcp-server"
      ],
      "env": {
        "ADX_CLUSTER_URL": "https://yourcluster.region.kusto.windows.net",
        "ADX_DATABASE": "your_database",
        "AZURE_TENANT_ID": "your_tenant_id",
        "AZURE_CLIENT_ID": "your_client_id",
        "ADX_TOKEN_FILE_PATH": "/var/run/secrets/azure/tokens/azure-identity-token"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `execute_query` | Выполнить KQL запрос к Azure Data Explorer |
| `list_tables` | Список всех таблиц в настроенной базе данных |
| `get_table_schema` | Получить схему для конкретной таблицы |
| `sample_table_data` | Получить примеры данных из таблицы |
| `get_table_details` | Получить статистику и метаданные таблицы |

## Возможности

- Выполнение KQL запросов со структурированными JSON результатами
- Обнаружение таблиц и просмотр схем с типами колонок
- Предварительный просмотр содержимого таблиц с настраиваемым размером выборки
- Получение статистики таблиц включая количество строк и размер хранилища
- Аутентификация DefaultAzureCredential с поддержкой Azure CLI и Managed Identity
- Встроенная поддержка Azure Workload Identity для AKS
- Множественные транспорты: stdio, HTTP и Server-Sent Events (SSE)
- Поддержка Docker с готовыми для продакшена образами контейнеров
- Поддержка Dev Container для GitHub Codespaces
- Настраиваемый список инструментов для контроля доступной функциональности

## Переменные окружения

### Обязательные
- `ADX_CLUSTER_URL` - URL кластера Azure Data Explorer
- `ADX_DATABASE` - Имя базы данных для подключения

### Опциональные
- `AZURE_TENANT_ID` - ID тенанта Azure AD
- `AZURE_CLIENT_ID` - ID клиента/приложения Azure AD
- `ADX_TOKEN_FILE_PATH` - Путь к файлу токена workload identity
- `ADX_MCP_SERVER_TRANSPORT` - Режим транспорта: stdio, http или sse
- `ADX_MCP_BIND_HOST` - Хост для привязки (только HTTP/SSE)
- `ADX_MCP_BIND_PORT` - Порт для привязки (только HTTP/SSE)
- `LOG_LEVEL` - Уровень логирования: DEBUG, INFO, WARNING, ERROR

## Примеры использования

```
Show me all tables in the database
```

```
What is the schema for the [table_name] table?
```

```
Give me a sample of data from [table_name]
```

```
Execute this KQL query: [your_kql_query]
```

```
Get statistics and metadata for [table_name]
```

## Ресурсы

- [GitHub Repository](https://github.com/pab1it0/adx-mcp-server)

## Примечания

Требует входа в Azure CLI с разрешениями на ADX кластер. Поддерживает кластеры Azure Data Explorer и Microsoft Fabric Eventhouse. По умолчанию использует WorkloadIdentityCredential в окружениях AKS, в противном случае откатывается к DefaultAzureCredential. Список инструментов настраивается для оптимизации использования контекстного окна.