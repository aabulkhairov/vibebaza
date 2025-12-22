---
title: ZapCap MCP сервер
description: MCP сервер, предоставляющий инструменты для загрузки видео, создания задач обработки и мониторинга их прогресса через ZapCap API для автоматической генерации субтитров и B-roll материалов.
tags:
- Media
- AI
- API
- Productivity
author: bogdanminko
featured: false
---

MCP сервер, предоставляющий инструменты для загрузки видео, создания задач обработки и мониторинга их прогресса через ZapCap API для автоматической генерации субтитров и B-roll материалов.

## Установка

### UV Tool

```bash
uv tool install zapcap-mcp-server
```

### Docker Hub

```bash
docker run --rm --init -i --net=host -v "/home/$USER:/host/home/$USER" -e "ZAPCAP_API_KEY=your_api_key_here" bogdan01m/zapcap-mcp-server:latest
```

## Конфигурация

### MCP Client (uvx)

```json
{
  "mcpServers": {
    "zapcap": {
      "command": "uvx",
      "args": ["zapcap-mcp-server"],
      "env": {
        "ZAPCAP_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Конфигурация Docker

```json
{
  "mcpServers": {
    "zapcap": {
      "command": "docker",
      "args": [
        "run", 
        "--rm", 
        "--init",
        "-i",
        "--net=host",
        "-v", "/home/$USER:/host/home/$USER",
        "-e", "ZAPCAP_API_KEY=your_api_key_here",
        "bogdan01m/zapcap-mcp-server:latest"
      ],
      "env": {
        "DOCKER_CLI_HINTS": "false"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `zapcap_mcp_upload_video` | Загрузить видеофайл в ZapCap |
| `zapcap_mcp_upload_video_by_url` | Загрузить видео по URL в ZapCap |
| `zapcap_mcp_get_templates` | Получить доступные шаблоны обработки из ZapCap |
| `zapcap_mcp_create_task` | Создать задачу обработки видео с полными возможностями настройки субтитров, стилизации и B-roll |
| `zapcap_mcp_monitor_task` | Отслеживать прогресс задачи обработки видео |

## Возможности

- Загрузка видео по пути к файлу или URL
- Создание задач обработки видео с полной настройкой
- Опции субтитров включая эмодзи, анимацию и выделение ключевых слов
- Настройка стиля для шрифта, цветов, теней и позиционирования
- Генерация B-roll с настраиваемым процентом
- Мониторинг прогресса задач
- Обработка на основе шаблонов
- Интерфейс на естественном языке вместо сложных API вызовов
- Автоматическое управление токенами
- Типобезопасность и валидация с интеграцией Pydantic

## Переменные окружения

### Обязательные
- `ZAPCAP_API_KEY` - API ключ для аутентификации на платформе ZapCap

## Примеры использования

```
Add green highlighted subtitles with 40% B-roll using viral template
```

## Ресурсы

- [GitHub Repository](https://github.com/bogdan01m/zapcap-mcp-server)

## Примечания

Это неофициальная реализация MCP Server для ZapCap. Требует API ключ ZapCap с https://platform.zapcap.ai/dashboard/api-key. Предоставляет преимущества по сравнению с прямым использованием API, включая управление токенами, интерфейс на естественном языке и валидацию типобезопасности.