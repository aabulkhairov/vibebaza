---
title: MCP Server Creator MCP сервер
description: Мета-сервер, который создает другие MCP серверы, предоставляя инструменты для динамической
  генерации конфигураций FastMCP серверов и Python кода.
tags:
- Code
- DevOps
- Productivity
- API
- Integration
author: GongRzhe
featured: false
---

Мета-сервер, который создает другие MCP серверы, предоставляя инструменты для динамической генерации конфигураций FastMCP серверов и Python кода.

## Установка

### pip

```bash
pip install mcp-server-creator
```

### uvx (рекомендуется)

```bash
uvx mcp-server-creator
```

### Python модуль

```bash
python -m mcp_server_creator
```

### Из исходного кода

```bash
git clone https://github.com/GongRzhe/mcp-server-creator.git
cd mcp-server-creator
pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mcp-server-creator": {
      "command": "uvx",
      "args": ["mcp-server-creator"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_server` | Создать новую конфигурацию MCP сервера |
| `list_servers` | Список всех конфигураций серверов в памяти |
| `get_server_details` | Получить детальную информацию о конкретном сервере |
| `add_tool` | Добавить инструмент к существующему серверу с поддержкой sync/async, кастомных параметров и автоматической им... |
| `add_resource` | Добавить ресурс к существующему серверу (статический или динамический с шаблонами и кастомными MIME типами) |
| `generate_server_code` | Сгенерировать полный Python код для сервера |
| `save_server` | Сохранить сгенерированный код сервера в файл |
| `create_example_server` | Создать полный пример Weather Service |

## Возможности

- Динамическое создание серверов: Создавайте новые конфигурации MCP серверов на лету
- Конструктор инструментов: Добавляйте кастомные инструменты с параметрами, типами возврата и реализациями
- Менеджер ресурсов: Добавляйте статические и динамические ресурсы с поддержкой шаблонов
- Генерация кода: Генерируйте полный, готовый к запуску Python код для ваших серверов
- Экспорт файлов: Сохраняйте сгенерированные серверы напрямую в Python файлы
- Примеры шаблонов: Встроенный пример сервера для демонстрации возможностей

## Примеры использования

```
Create a weather service MCP server with tools for getting current weather
```

```
Build custom API integration servers with dynamic tool generation
```

```
Generate MCP servers with both sync and async tools
```

```
Add resources to servers with template support
```

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/MCP-Server-Creator)

## Примечания

Требует Python 3.8+ и FastMCP >= 0.1.0. Может использоваться как MCP сервер и программно через Python API. Поддерживает как синхронные, так и асинхронные реализации инструментов.