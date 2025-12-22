---
title: Elasticsearch MCP сервер
description: Реализация сервера Model Context Protocol (MCP), которая обеспечивает взаимодействие с Elasticsearch
  и OpenSearch, позволяя искать документы, анализировать индексы и управлять кластерами
  через comprehensive набор инструментов.
tags:
- Database
- Search
- Analytics
- DevOps
- API
author: Community
featured: false
---

Реализация сервера Model Context Protocol (MCP), которая обеспечивает взаимодействие с Elasticsearch и OpenSearch, позволяя искать документы, анализировать индексы и управлять кластерами через comprehensive набор инструментов.

## Установка

### uvx (PyPI)

```bash
uvx elasticsearch-mcp-server
```

### uv (Локальная разработка)

```bash
uv --directory path/to/elasticsearch-mcp-server run elasticsearch-mcp-server
```

### SSE Transport

```bash
uvx elasticsearch-mcp-server --transport sse
# или с кастомными опциями
uvx elasticsearch-mcp-server --transport sse --host 0.0.0.0 --port 8000 --path /sse
```

### Streamable HTTP Transport

```bash
uvx elasticsearch-mcp-server --transport streamable-http
# или с кастомными опциями
uvx elasticsearch-mcp-server --transport streamable-http --host 0.0.0.0 --port 8000 --path /mcp
```

### Настройка Docker Compose

```bash
# Для Elasticsearch
docker-compose -f docker-compose-elasticsearch.yml up -d

# Для OpenSearch
docker-compose -f docker-compose-opensearch.yml up -d
```

## Конфигурация

### Claude Desktop (Elasticsearch с логином/паролем)

```json
{
  "mcpServers": {
    "elasticsearch-mcp-server": {
      "command": "uvx",
      "args": [
        "elasticsearch-mcp-server"
      ],
      "env": {
        "ELASTICSEARCH_HOSTS": "https://localhost:9200",
        "ELASTICSEARCH_USERNAME": "elastic",
        "ELASTICSEARCH_PASSWORD": "test123"
      }
    }
  }
}
```

### Claude Desktop (Elasticsearch с API ключом)

```json
{
  "mcpServers": {
    "elasticsearch-mcp-server": {
      "command": "uvx",
      "args": [
        "elasticsearch-mcp-server"
      ],
      "env": {
        "ELASTICSEARCH_HOSTS": "https://localhost:9200",
        "ELASTICSEARCH_API_KEY": "<YOUR_ELASTICSEARCH_API_KEY>"
      }
    }
  }
}
```

### Claude Desktop (OpenSearch)

```json
{
  "mcpServers": {
    "opensearch-mcp-server": {
      "command": "uvx",
      "args": [
        "opensearch-mcp-server"
      ],
      "env": {
        "OPENSEARCH_HOSTS": "https://localhost:9200",
        "OPENSEARCH_USERNAME": "admin",
        "OPENSEARCH_PASSWORD": "admin"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `general_api_request` | Выполнить общий HTTP API запрос для любого Elasticsearch/OpenSearch API, который не имеет выделенного... |
| `list_indices` | Список всех индексов |
| `get_index` | Возвращает информацию (маппинги, настройки, алиасы) об одном или нескольких индексах |
| `create_index` | Создать новый индекс |
| `delete_index` | Удалить индекс |
| `create_data_stream` | Создать новый поток данных (требует соответствующий шаблон индекса) |
| `get_data_stream` | Получить информацию об одном или нескольких потоках данных |
| `delete_data_stream` | Удалить один или несколько потоков данных и их базовые индексы |
| `search_documents` | Поиск документов |
| `index_document` | Создает или обновляет документ в индексе |
| `get_document` | Получить документ по ID |
| `delete_document` | Удалить документ по ID |
| `delete_by_query` | Удаляет документы, соответствующие предоставленному запросу |
| `get_cluster_health` | Возвращает базовую информацию о здоровье кластера |
| `get_cluster_stats` | Возвращает обзор статистики кластера высокого уровня |

## Возможности

- Comprehensive операции с индексами (список, создание, удаление, получение информации)
- Операции с документами (поиск, индексация, получение, удаление, удаление по запросу)
- Управление потоками данных (создание, получение, удаление)
- Мониторинг здоровья кластера и статистика
- Управление алиасами (список, создание, обновление, удаление)
- Поддержка как Elasticsearch, так и OpenSearch
- Множественные методы аутентификации (логин/пароль, API ключ)
- Контроль безопасности с отключением высокорисковых операций
- Множественные опции транспорта (stdio, SSE, streamable HTTP)
- Совместимость с Elasticsearch 7.x, 8.x и 9.x

## Переменные окружения

### Опциональные
- `ELASTICSEARCH_USERNAME` - Имя пользователя для базовой аутентификации
- `ELASTICSEARCH_PASSWORD` - Пароль для базовой аутентификации
- `OPENSEARCH_USERNAME` - Имя пользователя для базовой аутентификации OpenSearch
- `OPENSEARCH_PASSWORD` - Пароль для базовой аутентификации OpenSearch
- `ELASTICSEARCH_API_KEY` - API ключ для аутентификации Elasticsearch или Elastic Cloud (рекомендуется)
- `ELASTICSEARCH_HOSTS` - Список хостов через запятую (по умолчанию: https://localhost:9200)
- `OPENSEARCH_HOSTS` - Список хостов OpenSearch через запятую (по умолчанию: https://localhost:9200)
- `ELASTICSEARCH_VERIFY_CERTS` - Проверять ли SSL сертификаты (по умолчанию: false)

## Ресурсы

- [GitHub Repository](https://github.com/cr7258/elasticsearch-mcp-server)

## Примечания

Сервер поддерживает множественные версии Elasticsearch через различные варианты: elasticsearch-mcp-server-es7 (7.x), elasticsearch-mcp-server (8.x) и elasticsearch-mcp-server-es9 (9.x). Дефолтные учетные данные для тестовых кластеров: Elasticsearch (elastic/test123), OpenSearch (admin/admin). Kibana/OpenSearch Dashboards доступны по адресу http://localhost:5601. Высокорисковые операции могут быть отключены для безопасности в production окружениях.