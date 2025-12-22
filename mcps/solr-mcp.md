---
title: Solr MCP сервер
description: MCP сервер, который предоставляет возможности поиска документов через Apache Solr, позволяя большим языковым моделям искать и извлекать документы из коллекций Solr с продвинутыми функциями, такими как фасетный поиск и подсветка результатов.
tags:
- Search
- Database
- API
- Analytics
- Integration
author: Community
featured: false
install_command: mcp install src/server/mcp_server.py --name "Solr Search"
---

MCP сервер, который предоставляет возможности поиска документов через Apache Solr, позволяя большим языковым моделям искать и извлекать документы из коллекций Solr с продвинутыми функциями, такими как фасетный поиск и подсветка результатов.

## Установка

### UV Package Manager

```bash
uv install
```

### Pip

```bash
pip install -e .
```

### Настройка виртуального окружения

```bash
python -m venv .venv
source .venv/bin/activate  # On Linux/macOS
# OR
.\.venv\Scripts\activate   # On Windows
```

### Конфигурация окружения

```bash
cp .env.example .env
# Edit .env with your Solr connection details
```

### Запуск среды разработки Solr

```bash
./start_solr.sh
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search` | Расширенный поиск с фильтрацией, сортировкой, пагинацией, фасетированием и подсветкой |
| `get_document` | Получение конкретных документов по ID |

## Возможности

- MCP ресурсы для поиска документов Solr
- MCP инструменты для расширенного поиска и извлечения документов
- Поддержка фасетного поиска для исследования данных и агрегации
- Поддержка подсветки для показа где поисковые термины появляются в результатах
- Асинхронное взаимодействие с Solr используя httpx
- Типобезопасные интерфейсы с моделями Pydantic
- Поддержка аутентификации (JWT и OAuth 2.1)
- Комплексный набор тестов
- Docker-среда разработки Solr
- Нативная поддержка HTTP с потоковым HTTP транспортом

## Переменные окружения

### Обязательные
- `SOLR_BASE_URL` - Базовый URL для экземпляра Apache Solr
- `SOLR_COLLECTION` - Имя коллекции Solr для поиска

### Опциональные
- `MCP_SERVER_NAME` - Имя MCP сервера
- `MCP_SERVER_PORT` - Порт для MCP сервера
- `SOLR_USERNAME` - Имя пользователя для аутентификации Solr
- `SOLR_PASSWORD` - Пароль для аутентификации Solr
- `JWT_SECRET_KEY` - Секретный ключ для аутентификации JWT
- `JWT_ALGORITHM` - Алгоритм для токенов JWT
- `JWT_EXPIRATION_MINUTES` - Время истечения токена JWT в минутах
- `LOG_LEVEL` - Уровень логирования для сервера

## Примеры использования

```
Search for documents containing 'machine learning'
```

```
Find documents in the 'technology' category
```

```
Get documents sorted by date in descending order
```

```
Retrieve a specific document by its ID
```

```
Search with faceted results to explore data aggregations
```

## Ресурсы

- [GitHub Repository](https://github.com/mjochum64/mcp-solr-search)

## Примечания

Требует экземпляр Apache Solr. Включает настройку Docker Compose для разработки. Поддерживает OAuth 2.1 с Keycloak для продакшн развертываний. Версия 1.5.0 включает edismax многопольный поиск и функции автообновления OAuth. Всегда убеждайтесь, что виртуальное окружение активировано, чтобы избежать проблем с подключением.