---
title: kintone MCP сервер
description: MCP сервер для kintone, который позволяет исследовать и управлять данными kintone с помощью AI инструментов, таких как Claude Desktop.
tags:
- CRM
- Productivity
- API
- Integration
- Database
author: macrat
featured: false
---

MCP сервер для kintone, который позволяет исследовать и управлять данными kintone с помощью AI инструментов, таких как Claude Desktop.

## Установка

### Загрузка бинарного файла

```bash
Download the latest release from the release page: https://github.com/macrat/mcp-server-kintone/releases
You can place the executable file anywhere you like.
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "kintone": {
      "command": "C:\\path\\to\\mcp-server-kintone.exe",
      "env": {
        "KINTONE_BASE_URL": "https://<domain>.cybozu.com",
        "KINTONE_USERNAME": "<your username>",
        "KINTONE_PASSWORD": "<your password>",
        "KINTONE_API_TOKEN": "<your api token>, <another api token>, ...",
        "KINTONE_ALLOW_APPS": "1, 2, 3, ...",
        "KINTONE_DENY_APPS": "4, 5, ..."
      }
    }
  }
}
```

## Возможности

- Исследование данных kintone с помощью AI инструментов
- Управление данными kintone через естественный язык
- Поддержка аутентификации как по имени пользователя/паролю, так и через API токен
- Контроль доступа на уровне приложений с помощью списков разрешенных/запрещенных
- Интеграция с Claude Desktop и другими MCP клиентами

## Переменные окружения

### Обязательные
- `KINTONE_BASE_URL` - Базовый URL вашего kintone

### Опциональные
- `KINTONE_USERNAME` - Ваше имя пользователя для kintone
- `KINTONE_PASSWORD` - Ваш пароль для kintone
- `KINTONE_API_TOKEN` - API токены для kintone через запятую
- `KINTONE_ALLOW_APPS` - Список ID приложений через запятую, к которым разрешен доступ. По умолчанию разрешены все приложения.
- `KINTONE_DENY_APPS` - Список ID приложений через запятую, к которым запрещен доступ. Запрет имеет более высокий приоритет, чем разрешение.

## Примеры использования

```
What is the latest status of Customer A's project?
```

```
Update the progress of Project B to 50%.
```

```
Show me the projects that are behind schedule.
```

## Ресурсы

- [GitHub Repository](https://github.com/macrat/mcp-server-kintone)

## Примечания

Cybozu выпустила официальный kintone MCP сервер. Этот проект больше не будет добавлять новые функции, но будет поддерживать существующую функциональность до тех пор, пока официальный сервер не покроет те же возможности. Для аутентификации требуется либо комбинация имя пользователя/пароль, либо API токен. Конфигурационные файлы находятся по разным путям для разных операционных систем (MacOS/Linux: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: %APPDATA%\Claude\claude_desktop_config.json).