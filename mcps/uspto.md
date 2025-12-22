---
title: USPTO MCP сервер
description: MCP сервер для доступа к данным патентов и патентных заявок Ведомства по патентам и товарным знакам США (USPTO) через Patent Public Search API, Open Data Portal API и Google Patents Public Datasets via BigQuery.
tags:
- API
- Database
- Search
- Analytics
- Integration
author: Community
featured: false
---

MCP сервер для доступа к данным патентов и патентных заявок Ведомства по патентам и товарным знакам США (USPTO) через Patent Public Search API, Open Data Portal API и Google Patents Public Datasets via BigQuery.

## Установка

### Из исходного кода

```bash
git clone https://github.com/riemannzeta/patent_mcp_server
cd patent_mcp_server
uv sync
uv run patent-mcp-server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "patents": {
      "command": "uv",
      "args": [
        "--directory",
        "/Users/username/patent_mcp_server",
        "run",
        "patent-mcp-server"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `ppubs_search_patents` | Поиск выданных патентов в USPTO Public Search |
| `ppubs_search_applications` | Поиск опубликованных патентных заявок в USPTO Public Search |
| `ppubs_get_full_document` | Получение полной информации о патентном документе по GUID из ppubs.uspto.gov |
| `ppubs_get_patent_by_number` | Получение полного текста выданного патента по номеру из ppubs.uspto.gov |
| `ppubs_download_patent_pdf` | Скачивание выданного патента в формате PDF из ppubs.uspto.gov |
| `get_app` | Получение базовых данных патентной заявки |
| `search_applications` | Поиск патентных заявок с использованием параметров запроса |
| `download_applications` | Скачивание патентных заявок с использованием параметров запроса |
| `get_app_metadata` | Получение метаданных заявки |
| `get_app_adjustment` | Получение данных о корректировке срока патента |
| `get_app_assignment` | Получение данных о передаче прав |
| `get_app_attorney` | Получение информации об адвокате/агенте |
| `get_app_continuity` | Получение данных о преемственности |
| `get_app_foreign_priority` | Получение заявлений о зарубежном приоритете |
| `get_app_transactions` | Получение истории транзакций |

## Возможности

- Поиск патентов - Поиск патентов и патентных заявок в базах данных USPTO и Google Patents
- Полные текстовые документы - Получение полного текста патентов, включая формулу изобретения, описание и т.д.
- Скачивание PDF - Скачивание патентов в формате PDF
- Метаданные - Доступ к библиографической информации патентов, переуступкам и данным судебных разбирательств
- Интеграция с Google Patents - Доступ к 90+ млн патентных публикаций из 17+ стран через BigQuery
- Расширенный поиск - Поиск по изобретателю, правообладателю, классификации CPC и другим параметрам

## Переменные окружения

### Обязательные
- `USPTO_API_KEY` - API ключ Open Data Portal (ODP) для доступа к инструментам api.uspto.gov

### Опциональные
- `GOOGLE_CLOUD_PROJECT` - ID проекта Google Cloud для доступа к BigQuery
- `GOOGLE_APPLICATION_CREDENTIALS` - Путь к JSON файлу ключа сервисного аккаунта Google Cloud
- `BIGQUERY_DATASET` - Идентификатор датасета BigQuery
- `BIGQUERY_LOCATION` - Местоположение BigQuery
- `BIGQUERY_QUERY_TIMEOUT` - Таймаут запроса BigQuery в секундах
- `BIGQUERY_MAX_RESULTS` - Максимальное количество результатов BigQuery
- `LOG_LEVEL` - Уровень логирования (DEBUG, INFO, WARNING, ERROR, CRITICAL)
- `REQUEST_TIMEOUT` - Таймаут запроса в секундах

## Ресурсы

- [GitHub Repository](https://github.com/riemannzeta/patent_mcp_server)

## Примечания

Требует Python 3.10-3.13 (рекомендуется 3.12), UV для управления зависимостями и API ключи для USPTO ODP и Google Cloud BigQuery. Некоторые инструменты требуют настройки Google Cloud с включенным BigQuery API. Действуют лимиты скорости для Patent Public Search API. Клиент Claude Desktop не полностью поддерживает все инструменты (например, скачивание PDF).