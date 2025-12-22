---
title: Vega-Lite MCP сервер
description: MCP сервер, который предоставляет интерфейс для визуализации данных с помощью синтаксиса Vega-Lite, позволяя LLM сохранять таблицы данных и создавать визуализации.
tags:
- Analytics
- Productivity
- API
author: Community
featured: false
---

MCP сервер, который предоставляет интерфейс для визуализации данных с помощью синтаксиса Vega-Lite, позволяя LLM сохранять таблицы данных и создавать визуализации.

## Установка

### UV с директорией

```bash
uv --directory /absolute/path/to/mcp-datavis-server run mcp_server_datavis --output_type png
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "datavis": {
        "command": "uv",
        "args": [
            "--directory",
            "/absolute/path/to/mcp-datavis-server",
            "run",
            "mcp_server_datavis",
            "--output_type",
            "png" # or "text"
        ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `save_data` | Сохранить таблицу агрегированных данных на сервер для последующей визуализации |
| `visualize_data` | Визуализировать таблицу данных с помощью синтаксиса Vega-Lite |

## Возможности

- Сохранение таблиц данных для визуализации
- Создание визуализаций с использованием синтаксиса Vega-Lite
- Вывод визуализаций в виде текста (JSON) или PNG изображений
- Поддержка вывода PNG изображений в кодировке base64
- Полная спецификация Vega-Lite с интеграцией данных

## Ресурсы

- [GitHub Repository](https://github.com/isaacwasserman/mcp-vegalite-server)

## Примечания

Сервер поддерживает два типа вывода: 'text', который возвращает спецификацию Vega-Lite с данными, и 'png', который возвращает изображения PNG в кодировке base64. Сервер требует указания абсолютного пути к директории mcp-datavis-server.