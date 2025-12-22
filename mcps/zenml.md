---
title: ZenML MCP сервер
description: MCP сервер, который предоставляет доступ на чтение к ZenML API для управления ML и AI пайплайнами, позволяя взаимодействовать с пользователями, стеками, пайплайнами, запусками, сервисами, артефактами и многим другим.
tags:
- AI
- DevOps
- Cloud
- Analytics
- Integration
author: zenml-io
featured: false
---

MCP сервер, который предоставляет доступ на чтение к ZenML API для управления ML и AI пайплайнами, позволяя взаимодействовать с пользователями, стеками, пайплайнами, запусками, сервисами, артефактами и многим другим.

## Установка

### Из исходного кода

```bash
git clone https://github.com/zenml-io/mcp-zenml.git
```

### Docker Hub

```bash
docker pull zenmldocker/mcp-zenml:latest
```

### Запуск Docker

```bash
docker run -i --rm \
  -e ZENML_STORE_URL="https://your-zenml-server.example.com" \
  -e ZENML_STORE_API_KEY="your-api-key" \
  zenmldocker/mcp-zenml:latest
```

### Локальная сборка

```bash
docker build -t zenmldocker/mcp-zenml:local .
```

### MCP Bundle

```bash
Перетащите файл mcp-zenml.mcpb в настройки Claude Desktop
```

## Конфигурация

### Claude Desktop / Cursor

```json
{
    "mcpServers": {
        "zenml": {
            "command": "/usr/local/bin/uv",
            "args": ["run", "path/to/server/zenml_server.py"],
            "env": {
                "LOGLEVEL": "WARNING",
                "NO_COLOR": "1",
                "ZENML_LOGGING_COLORS_DISABLED": "true",
                "ZENML_LOGGING_VERBOSITY": "WARN",
                "ZENML_ENABLE_RICH_TRACEBACK": "false",
                "PYTHONUNBUFFERED": "1",
                "PYTHONIOENCODING": "UTF-8",
                "ZENML_STORE_URL": "https://your-zenml-server-goes-here.com",
                "ZENML_STORE_API_KEY": "your-api-key-here"
            }
        }
    }
}
```

### Конфигурация Docker

```json
{
  "mcpServers": {
    "zenml": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm",
        "-e", "ZENML_STORE_URL=https://...",
        "-e", "ZENML_STORE_API_KEY=ZENKEY_...",
        "-e", "ZENML_ACTIVE_PROJECT_ID=...",
        "-e", "LOGLEVEL=WARNING",
        "-e", "NO_COLOR=1",
        "-e", "ZENML_LOGGING_COLORS_DISABLED=true",
        "-e", "ZENML_LOGGING_VERBOSITY=WARN",
        "-e", "ZENML_ENABLE_RICH_TRACEBACK=false",
        "-e", "PYTHONUNBUFFERED=1",
        "-e", "PYTHONIOENCODING=UTF-8",
        "zenmldocker/mcp-zenml:latest"
      ]
    }
  }
}
```

## Возможности

- Доступ к основному функционалу чтения с ZenML сервера
- Получение информации о пользователях, стеках, пайплайнах и запусках пайплайнов
- Доступ к шагам пайплайнов, сервисам, компонентам стеков и флейворам
- Просмотр шаблонов запуска пайплайнов и расписаний
- Доступ к метаданным артефактов (не к самим данным)
- Управление коннекторами сервисов
- Просмотр кода шагов и логов шагов (для облачных стеков)
- Запуск новых пайплайнов (если присутствует шаблон запуска)
- Автоматическое smoke тестирование каждые 3 дня
- Быстрый CI с кэшированием UV

## Переменные окружения

### Обязательные
- `ZENML_STORE_URL` - URL вашего ZenML сервера
- `ZENML_STORE_API_KEY` - API ключ для вашего ZenML сервера

### Опциональные
- `ZENML_ACTIVE_PROJECT_ID` - ID активного проекта для ZenML
- `LOGLEVEL` - Уровень логирования
- `NO_COLOR` - Отключить цветной вывод
- `ZENML_LOGGING_COLORS_DISABLED` - Отключить цвета в логах ZenML
- `ZENML_LOGGING_VERBOSITY` - Уровень детализации логирования ZenML
- `ZENML_ENABLE_RICH_TRACEBACK` - Включить rich трейсбеки в ZenML
- `PYTHONUNBUFFERED` - Небуферизованный вывод Python
- `PYTHONIOENCODING` - Кодировка ввода-вывода Python

## Ресурсы

- [Репозиторий GitHub](https://github.com/zenml-io/mcp-zenml)

## Примечания

Это beta/экспериментальный релиз. Вам нужен доступ к развернутому ZenML серверу (бесплатная пробная версия доступна в ZenML Pro). Сервер опубликован в официальном Anthropic MCP Registry и автоматически обновляется с каждым тегированным релизом. Для лучшего отображения результатов инструментов ZenML в Claude Desktop добавьте предпочтение форматирования JSON ответов как markdown таблиц. Требует UV для локальной разработки.