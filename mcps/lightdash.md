---
title: Lightdash MCP сервер
description: MCP сервер, который предоставляет доступ к API Lightdash, позволяя AI-ассистентам взаимодействовать с вашими данными Lightdash через стандартизированный интерфейс.
tags:
- Analytics
- API
- Integration
- Database
- Productivity
author: Community
featured: false
install_command: npx -y @smithery/cli install lightdash-mcp-server --client claude
---

MCP сервер, который предоставляет доступ к API Lightdash, позволяя AI-ассистентам взаимодействовать с вашими данными Lightdash через стандартизированный интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install lightdash-mcp-server --client claude
```

### NPM

```bash
npm install lightdash-mcp-server
```

### NPX (Stdio)

```bash
npx lightdash-mcp-server
```

### NPX (HTTP)

```bash
npx lightdash-mcp-server -port 8080
```

## Конфигурация

### Claude Desktop (Stdio)

```json
{
  "lightdash": {
    "command": "npx",
    "args": [
      "-y",
      "lightdash-mcp-server"
    ],
    "env": {
      "LIGHTDASH_API_KEY": "<your PAT>",
      "LIGHTDASH_API_URL": "https://<your base url>"
    }
  }
}
```

### Claude Desktop (HTTP)

```json
{
  "lightdash": {
    "url": "http://localhost:8080/mcp"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_projects` | Получить список всех проектов в организации Lightdash |
| `get_project` | Получить подробную информацию о конкретном проекте |
| `list_spaces` | Получить список всех пространств в проекте |
| `list_charts` | Получить список всех графиков в проекте |
| `list_dashboards` | Получить список всех дашбордов в проекте |
| `get_custom_metrics` | Получить пользовательские метрики для проекта |
| `get_catalog` | Получить каталог для проекта |
| `get_metrics_catalog` | Получить каталог метрик для проекта |
| `get_charts_as_code` | Получить графики в виде кода для проекта |
| `get_dashboards_as_code` | Получить дашборды в виде кода для проекта |

## Возможности

- Доступ к проектам Lightdash и их подробностям
- Просмотр и управление пространствами внутри проектов
- Доступ к графикам и дашбордам
- Получение пользовательских метрик и информации каталога
- Экспорт графиков и дашбордов в виде кода
- Поддержка режимов транспорта Stdio и HTTP
- Интеграция с API Lightdash через PAT аутентификацию

## Переменные окружения

### Обязательные
- `LIGHTDASH_API_KEY` - Ваш токен PAT (Personal Access Token) для Lightdash
- `LIGHTDASH_API_URL` - Базовый URL API для вашего экземпляра Lightdash

## Ресурсы

- [GitHub Repository](https://github.com/syucream/lightdash-mcp-server)

## Примечания

Поддерживает два режима транспорта: Stdio (по умолчанию) и HTTP. Режим HTTP обслуживает запросы на эндпойнте /mcp и требует установки переменных окружения на стороне сервера. Включает скрипты для разработки и примеры реализации для программного доступа.