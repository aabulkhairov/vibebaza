---
title: Outline MCP сервер
description: MCP сервер для взаимодействия с системами управления документами Outline, позволяющий искать, создавать, редактировать и управлять документами и коллекциями с автоматическим ограничением скорости запросов.
tags:
- Productivity
- API
- Storage
- Search
- Integration
author: Vortiago
featured: false
---

MCP сервер для взаимодействия с системами управления документами Outline, позволяющий искать, создавать, редактировать и управлять документами и коллекциями с автоматическим ограничением скорости запросов.

## Установка

### uv (Рекомендуется)

```bash
uvx mcp-outline
```

### pip

```bash
pip install mcp-outline
```

### Docker

```bash
docker run -e OUTLINE_API_KEY=<your-key> ghcr.io/vortiago/mcp-outline:latest
```

### Docker из исходников

```bash
docker buildx build -t mcp-outline .
docker run -e OUTLINE_API_KEY=<your-key> mcp-outline
```

### Настройка для разработки

```bash
git clone https://github.com/Vortiago/mcp-outline.git
cd mcp-outline
uv pip install -e ".[dev]"
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mcp-outline": {
      "command": "uvx",
      "args": ["mcp-outline"],
      "env": {
        "OUTLINE_API_KEY": "<YOUR_API_KEY>",
        "OUTLINE_API_URL": "<YOUR_OUTLINE_URL>"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcp-outline": {
    "command": "uvx",
    "args": ["mcp-outline"],
    "env": {
      "OUTLINE_API_KEY": "<YOUR_API_KEY>",
      "OUTLINE_API_URL": "<YOUR_OUTLINE_URL>"
    }
  }
}
```

### VS Code

```json
{
  "servers": {
    "mcp-outline": {
      "type": "stdio",
      "command": "uvx",
      "args": ["mcp-outline"],
      "env": {
        "OUTLINE_API_KEY": "<YOUR_API_KEY>"
      }
    }
  }
}
```

### Cline (VS Code)

```json
{
  "mcp-outline": {
    "command": "uvx",
    "args": ["mcp-outline"],
    "env": {
      "OUTLINE_API_KEY": "<YOUR_API_KEY>",
      "OUTLINE_API_URL": "<YOUR_OUTLINE_URL>"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_documents` | Поиск документов по ключевым словам с пагинацией |
| `list_collections` | Список всех коллекций |
| `get_collection_structure` | Получение иерархии документов в коллекции |
| `get_document_id_from_title` | Поиск ID документа по названию |
| `read_document` | Получение содержимого документа |
| `export_document` | Экспорт документа в формате markdown |
| `create_document` | Создание нового документа |
| `update_document` | Обновление документа (доступен режим добавления) |
| `move_document` | Перемещение документа в другую коллекцию или к другому родителю |
| `archive_document` | Архивирование документа |
| `unarchive_document` | Восстановление документа из архива |
| `delete_document` | Удаление документа (или перемещение в корзину) |
| `restore_document` | Восстановление документа из корзины |
| `list_archived_documents` | Список всех архивированных документов |
| `list_trash` | Список всех документов в корзине |

## Возможности

- Операции с документами: поиск, чтение, создание, редактирование, архивирование документов
- Коллекции: список, создание, управление иерархиями документов
- Комментарии: добавление и просмотр древовидных комментариев
- Обратные ссылки: поиск документов, ссылающихся на конкретный документ
- MCP ресурсы: прямой доступ к содержимому через URI
- Автоматическое ограничение скорости: прозрачная обработка лимитов API с логикой повторных попыток

## Переменные окружения

### Обязательные
- `OUTLINE_API_KEY` - API ключ из веб-интерфейса Outline (Настройки → API Keys → Create New)

### Опциональные
- `OUTLINE_API_URL` - URL эндпоинта Outline API
- `OUTLINE_READ_ONLY` - Включение режима только для чтения, отключающего все операции записи
- `OUTLINE_DISABLE_DELETE` - Отключение только операций удаления
- `OUTLINE_DISABLE_AI_TOOLS` - Отключение AI инструментов для экземпляров без OpenAI
- `MCP_TRANSPORT` - Режим транспорта: stdio (локальный), sse или streamable-http (удаленный)
- `MCP_HOST` - Хост сервера (используйте 0.0.0.0 в Docker для внешних подключений)
- `MCP_PORT` - Порт HTTP сервера для режимов sse и streamable-http

## Примеры использования

```
Поиск документов, содержащих определенные ключевые слова
```

```
Создание новых документов в коллекциях с иерархической структурой
```

```
Экспорт документов и коллекций в формате markdown
```

```
Добавление древовидных комментариев к документам
```

```
Поиск обратных ссылок для просмотра того, какие документы ссылаются на другие
```

## Ресурсы

- [GitHub Repository](https://github.com/Vortiago/mcp-outline)

## Примечания

Требует аккаунт Outline (облачный хостинг или самостоятельный хостинг). Поддерживает как режим только для чтения, так и полный доступ. Включает автоматическое ограничение скорости с экспоненциальной задержкой повторных попыток. Предоставляет MCP ресурсы для прямого доступа к содержимому через URI. Совместим с деплоем в Docker и несколькими режимами транспорта.