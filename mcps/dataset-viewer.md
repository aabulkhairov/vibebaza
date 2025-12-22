---
title: Dataset Viewer MCP сервер
description: MCP сервер для работы с API Hugging Face Dataset Viewer, предоставляющий возможности просматривать, анализировать, искать и фильтровать датасеты, размещённые на Hugging Face Hub.
tags:
- AI
- Analytics
- API
- Search
- Database
author: privetin
featured: false
---

MCP сервер для работы с API Hugging Face Dataset Viewer, предоставляющий возможности просматривать, анализировать, искать и фильтровать датасеты, размещённые на Hugging Face Hub.

## Установка

### Из исходников

```bash
git clone https://github.com/privetin/dataset-viewer.git
cd dataset-viewer
uv venv
source .venv/bin/activate
uv add -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "dataset-viewer": {
      "command": "uv",
      "args": [
        "--directory",
        "parent_to_repo/dataset-viewer",
        "run",
        "dataset-viewer"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `validate` | Проверяет, существует ли датасет и доступен ли он |
| `get_info` | Получает подробную информацию о датасете |
| `get_rows` | Получает содержимое датасета с пагинацией |
| `get_first_rows` | Получает первые строки из раздела датасета |
| `get_statistics` | Получает статистику по разделу датасета |
| `search_dataset` | Поиск текста в датасете |
| `filter` | Фильтрует строки, используя SQL-подобные условия |
| `get_parquet` | Скачивает полный датасет в формате Parquet |

## Возможности

- Использует схему URI dataset:// для доступа к датасетам Hugging Face
- Поддерживает конфигурации датасетов и разделы
- Предоставляет доступ к содержимому датасета с пагинацией
- Обрабатывает аутентификацию для приватных датасетов
- Поддерживает поиск и фильтрацию содержимого датасета
- Предоставляет статистику и анализ датасета

## Переменные окружения

### Опциональные
- `HUGGINGFACE_TOKEN` - Ваш API токен Hugging Face для доступа к приватным датасетам

## Ресурсы

- [GitHub Repository](https://github.com/privetin/dataset-viewer)

## Примечания

Требует Python 3.12 или выше и установщик пакетов uv. Лицензия MIT.