---
title: 1Panel MCP сервер
description: MCP сервер для работы с 1Panel — веб-инструментом управления Linux-серверами.
  Позволяет управлять сайтами, базами данных, приложениями и системными ресурсами через
  естественный язык.
tags:
- DevOps
- Database
- Monitoring
- Integration
- Productivity
author: 1Panel-dev
featured: true
---

MCP сервер для работы с 1Panel — веб-инструментом управления Linux-серверами. Позволяет управлять сайтами, базами данных, приложениями и системными ресурсами через естественный язык.

## Установка

### Скачать из Release

```bash
chmod +x mcp-1panel-linux-amd64
mv mcp-1panel-linux-amd64 /usr/local/bin/mcp-1panel
```

### Сборка из исходников

```bash
git clone https://github.com/1Panel-dev/mcp-1panel.git
cd mcp-1panel
make build
```

### Go Install

```bash
go install github.com/1Panel-dev/mcp-1panel@latest
```

### Docker

```bash
docker run -i --rm -e PANEL_HOST -e PANEL_ACCESS_TOKEN 1panel/1panel-mcp-server
```

## Конфигурация

### Cursor/Windsurf — локальный бинарник

```json
{
  "mcpServers": {
    "mcp-1panel": {
      "command": "mcp-1panel",
      "env": {
        "PANEL_ACCESS_TOKEN": "<your 1Panel access token>",
        "PANEL_HOST": "such as http://localhost:8080"
      }
    }
  }
}
```

### Cursor/Windsurf — Docker

```json
{
  "mcpServers": {
    "mcp-1panel": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "PANEL_HOST",
        "-e",
        "PANEL_ACCESS_TOKEN",
        "1panel/1panel-mcp-server"
      ],
      "env": {
        "PANEL_HOST": "such as http://localhost:8080",
        "PANEL_ACCESS_TOKEN": "<your 1Panel access token>"
      }
    }
  }
}
```

### Cursor/Windsurf — SSE режим

```json
{
  "mcpServers": {
    "mcp-1panel": {
      "url": "http://localhost:8000/sse"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_dashboard_info` | Получить статус дашборда |
| `get_system_info` | Получить информацию о системе |
| `list_websites` | Список всех сайтов |
| `create_website` | Создать сайт |
| `list_ssls` | Список всех сертификатов |
| `create_ssl` | Создать сертификат |
| `list_installed_apps` | Список установленных приложений |
| `install_openresty` | Установить OpenResty |
| `install_mysql` | Установить MySQL |
| `list_databases` | Список всех баз данных |
| `create_database` | Создать базу данных |

## Возможности

- Поддержка stdio и SSE режимов транспорта
- Мультиархитектурная поддержка Docker (amd64, arm64, arm/v7, s390x, ppc64le)
- Управление сайтами
- Управление SSL-сертификатами
- Создание и просмотр баз данных
- Установка и управление приложениями
- Мониторинг системы и информация о дашборде
- Интеграция с интерфейсом управления 1Panel

## Переменные окружения

### Обязательные
- `PANEL_ACCESS_TOKEN` — токен доступа 1Panel для аутентификации
- `PANEL_HOST` — адрес сервера 1Panel (например, http://localhost:8080)

## Ресурсы

- [GitHub Repository](https://github.com/1Panel-dev/mcp-1panel)

## Примечания

Для сборки из исходников требуется Go 1.23 или выше. Сервер можно запустить в SSE режиме командой: mcp-1panel -host http://localhost:8080 -token <token> -transport sse -addr http://localhost:8000
