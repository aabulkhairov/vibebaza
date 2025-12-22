---
title: CockroachDB MCP сервер
description: Промышленный Model Context Protocol (MCP) сервер, который использует CockroachDB
  в качестве надежного бэкенда для управления контекстами моделей с полными CRUD операциями и
  JSONB хранилищем.
tags:
- Database
- API
- AI
- Storage
- DevOps
author: Community
featured: false
---

Промышленный Model Context Protocol (MCP) сервер, который использует CockroachDB в качестве надежного бэкенда для управления контекстами моделей с полными CRUD операциями и JSONB хранилищем.

## Установка

### PyPI

```bash
pip install cockroachdb-mcp-server
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_context` | Создать новый контекст модели |
| `list_contexts` | Получить список всех контекстов |
| `get_context` | Получить контекст по ID |
| `update_context` | Обновить существующий контекст |
| `delete_context` | Удалить контекст по ID |

## Возможности

- REST API для управления MCP контекстами
- Инициализация схемы через CLI флаг или переменную окружения
- Автоопределение CRDB URL и исправление диалекта
- Структурированное логирование с настраиваемым уровнем
- JSONB хранилище, позволяющее произвольные схемы входных/выходных данных
- Готов для расширений /run, /deploy, /evaluate

## Переменные окружения

### Обязательные
- `CRDB_URL` - URL подключения к CockroachDB (поддерживает форматы postgresql:// и cockroachdb://)

### Опциональные
- `MCP_AUTO_INIT_SCHEMA` - Автоматически инициализировать схему базы данных при запуске

## Ресурсы

- [GitHub Repository](https://github.com/viragtripathi/cockroachdb-mcp-server)

## Примечания

Сервер по умолчанию работает на http://localhost:8081. Бесшовно работает с CLI инструментом cockroachdb-mcp-client. Включает автоматическое создание схемы с UUID первичными ключами и JSONB хранилищем контекстов.