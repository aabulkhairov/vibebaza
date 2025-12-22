---
title: ArangoDB Graph MCP сервер
description: Готовый к продакшену MCP сервер, предоставляющий продвинутые операции ArangoDB для AI-ассистентов с асинхронной архитектурой Python, комплексным управлением графами, гибким конвертированием контента, функциональностью резервного копирования/восстановления и аналитическими возможностями.
tags:
- Database
- Analytics
- Storage
- API
- Code
author: Community
featured: false
---

Готовый к продакшену MCP сервер, предоставляющий продвинутые операции ArangoDB для AI-ассистентов с асинхронной архитектурой Python, комплексным управлением графами, гибким конвертированием контента, функциональностью резервного копирования/восстановления и аналитическими возможностями.

## Установка

### PyPI

```bash
pip install mcp-arangodb-async
```

### Настройка Docker

```bash
docker run -d \
  --name arangodb \
  -p 8529:8529 \
  -e ARANGO_ROOT_PASSWORD=changeme \
  arangodb:3.11
```

### Проверка здоровья

```bash
python -m mcp_arangodb_async --health
```

### Сборка Docker контейнера

```bash
docker build -t mcp-arangodb-async:latest .
```

### HTTP сервер

```bash
python -m mcp_arangodb_async --transport http --host 0.0.0.0 --port 8000
```

## Конфигурация

### Claude Desktop (stdio)

```json
{
  "mcpServers": {
    "arangodb": {
      "command": "python",
      "args": ["-m", "mcp_arangodb_async", "server"],
      "env": {
        "ARANGO_URL": "http://localhost:8529",
        "ARANGO_DB": "mcp_arangodb_test",
        "ARANGO_USERNAME": "mcp_arangodb_user",
        "ARANGO_PASSWORD": "mcp_arangodb_password"
      }
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "arangodb": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "mcp-arangodb-async:latest"],
      "env": {
        "ARANGO_URL": "http://host.docker.internal:8529",
        "ARANGO_DB": "mcp_arangodb_test",
        "ARANGO_USERNAME": "mcp_arangodb_user",
        "ARANGO_PASSWORD": "mcp_arangodb_password"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `arango_query` | Выполнить AQL запросы |
| `arango_list_collections` | Список всех коллекций |
| `arango_insert` | Вставить документы |
| `arango_update` | Обновить документы |
| `arango_remove` | Удалить документы |
| `arango_create_collection` | Создать коллекции |
| `arango_backup` | Резервное копирование коллекций |
| `arango_list_indexes` | Список индексов |
| `arango_create_index` | Создать индексы |
| `arango_delete_index` | Удалить индексы |
| `arango_explain_query` | Объяснить план выполнения запроса |
| `arango_query_builder` | Построить AQL запросы |
| `arango_query_profile` | Профилировать производительность запросов |
| `arango_validate_references` | Валидировать ссылки документов |
| `arango_insert_with_validation` | Вставка с валидацией |

## Возможности

- 43 MCP инструмента - Полные операции ArangoDB (запросы, коллекции, индексы, графы)
- Паттерны дизайна MCP - Прогрессивное обнаружение, переключение контекста, выгрузка инструментов (экономия токенов 98.7%)
- Управление графами - Создание, обход, резервное копирование/восстановление именованных графов
- Конвертация контента - Форматы JSON, Markdown, YAML и таблиц
- Резервное копирование/восстановление - Резервное копирование на уровне коллекций и графов с валидацией
- Аналитика - Профилирование запросов, планы объяснения, статистика графов
- Двойной транспорт - stdio (десктопные клиенты) и HTTP (веб/контейнеризованные)
- Поддержка Docker - Запуск в Docker для изоляции и воспроизводимости
- Готов к продакшену - Логика повторных попыток, плавная деградация, комплексная обработка ошибок
- Типобезопасный - Валидация Pydantic для всех аргументов инструментов

## Переменные окружения

### Обязательные
- `ARANGO_URL` - URL подключения ArangoDB
- `ARANGO_DB` - Имя базы данных
- `ARANGO_USERNAME` - Имя пользователя базы данных
- `ARANGO_PASSWORD` - Пароль базы данных

### Опциональные
- `MCP_TRANSPORT` - Тип транспорта (stdio или http)
- `MCP_HTTP_HOST` - Адрес привязки HTTP
- `MCP_HTTP_PORT` - HTTP порт
- `MCP_HTTP_STATELESS` - Режим без состояния
- `ARANGO_TIMEOUT_SEC` - Таймаут запроса
- `ARANGO_CONNECT_RETRIES` - Повторные попытки подключения
- `ARANGO_CONNECT_DELAY_SEC` - Задержка повторных попыток
- `LOG_LEVEL` - Уровень логирования (DEBUG, INFO, WARNING, ERROR)

## Примеры использования

```
Показать все коллекции в базе данных ArangoDB
```

```
Создать граф под названием 'codebase' с коллекциями вершин 'modules' и 'functions', и коллекцией рёбер 'calls', соединяющей функции
```

```
Вставить эти модули в коллекцию 'modules'
```

```
Найти все функции, которые зависят от модуля 'auth', используя обход графа
```

```
Проверить циклические зависимости в графе кодовой базы
```

## Ресурсы

- [GitHub Repository](https://github.com/PCfVW/mcp-arangodb-async)

## Примечания

Требует Python 3.11+ и Docker Desktop для ArangoDB. Сервер предоставляет комплексные возможности анализа графов, включая анализ зависимостей кодовой базы, обнаружение циклических ссылок и визуализацию архитектуры. Поддерживает как stdio, так и HTTP транспорты для различных сценариев деплоя.