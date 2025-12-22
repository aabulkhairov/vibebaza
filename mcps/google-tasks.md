---
title: Google Tasks MCP сервер
description: Этот MCP сервер интегрируется с Google Tasks для просмотра, чтения, поиска, создания, обновления и удаления задач.
tags:
- Productivity
- API
- Cloud
- Integration
author: zcaceres
featured: false
---

Этот MCP сервер интегрируется с Google Tasks для просмотра, чтения, поиска, создания, обновления и удаления задач.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @zcaceres/gtasks --client claude
```

### Из исходного кода

```bash
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "gtasks": {
      "command": "/opt/homebrew/bin/node",
      "args": [
        "{ABSOLUTE PATH TO FILE HERE}/dist/index.js"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search` | Поиск задач в Google Tasks |
| `list` | Просмотр всех задач в Google Tasks с опциональной пагинацией |
| `create` | Создание новой задачи в Google Tasks с названием, заметками и датой выполнения |
| `update` | Обновление существующей задачи в Google Tasks, включая название, заметки, статус и дату выполнения |
| `delete` | Удаление задачи в Google Tasks |
| `clear` | Очистка выполненных задач из списка задач Google Tasks |

## Возможности

- Поиск задач в Google Tasks
- Просмотр всех задач с поддержкой пагинации
- Создание новых задач с названием, заметками и датами выполнения
- Обновление существующих задач, включая изменение статуса
- Удаление отдельных задач
- Очистка выполненных задач из списков задач
- Доступ к ресурсам задач через gtasks:// URI
- Полные метаданные задач, включая название, статус, дату выполнения и заметки

## Ресурсы

- [GitHub Repository](https://github.com/zcaceres/gtasks-mcp)

## Примечания

Требует настройки проекта Google Cloud с конфигурацией OAuth. Необходимо создать файл gcp-oauth.keys.json с учетными данными OAuth клиента. Аутентификация требует запуска 'npm run start auth' для завершения OAuth процесса в браузере. Учетные данные сохраняются как .gdrive-server-credentials.json. Требует области действия Google Tasks API: https://www.googleapis.com/auth/tasks