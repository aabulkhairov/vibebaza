---
title: TeamRetro MCP сервер
description: MCP сервер, который обеспечивает AI-интеграцию с платформой TeamRetro, позволяя бесшовно взаимодействовать с управлением командами, ретроспективами, проверками состояния и другими функциями TeamRetro через стандартизированные MCP инструменты.
tags:
- Productivity
- API
- Integration
- Analytics
- CRM
author: adepanges
featured: false
install_command: npx -y @smithery/cli install @adepanges/teamretro-mcp-server --client
  claude
---

MCP сервер, который обеспечивает AI-интеграцию с платформой TeamRetro, позволяя бесшовно взаимодействовать с управлением командами, ретроспективами, проверками состояния и другими функциями TeamRetro через стандартизированные MCP инструменты.

## Установка

### NPX

```bash
npx -y teamretro-mcp-server
```

### Smithery

```bash
npx -y @smithery/cli install @adepanges/teamretro-mcp-server --client claude
```

### Из исходного кода

```bash
git clone https://github.com/adepanges/teamretro-mcp-server.git
cd teamretro-mcp-server
npm install
npm run build
```

## Конфигурация

### Конфигурация NPX

```json
{
  "mcpServers": {
    "teamretro-mcp-server": {
      "command": "npx",
      "args": ["-y", "teamretro-mcp-server"],
      "env": {
        "TEAMRETRO_AUTH_TYPE": "apiKey",
        "TEAMRETRO_API_KEY": "your-api-key"
      }
    }
  }
}
```

### Конфигурация из исходного кода

```json
{
  "mcpServers": {
    "teamretro-mcp-server": {
      "command": "node",
      "args": ["/path/to/teamretro-mcp-server/dist/index.js"],
      "env": {
        "TEAMRETRO_AUTH_TYPE": "apiKey",
        "TEAMRETRO_API_KEY": "your-api-key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_users` | Получение списка пользователей с пагинацией, используя параметры offset и limit для контроля количества возвращаемых результатов... |
| `add_user` | Добавление нового пользователя или обновление информации существующего пользователя по его email адресу, с указанием дополнительных параметров... |
| `update_user` | Обновление данных существующего пользователя, таких как имя и emailAddress, предоставив их текущие данные... |
| `delete_user` | Удаление пользователя по его email адресу |
| `get_user` | Получение подробной информации об одном пользователе по его email адресу |
| `list_teams` | Получение списка команд из TeamRetro с фильтрацией по тегам и ID, и пагинацией, используя параметры offset и limit... |
| `detail_team` | Получение подробной информации об одной команде по её уникальному ID |
| `update_team` | Обновление данных существующей команды, таких как имя и связанные теги, предоставив ID команды |
| `create_team` | Создание новой команды с обязательным именем и опциональными тегами и участниками |
| `delete_team` | Удаление существующей команды по её ID |
| `list_team_members` | Получение списка участников команды для указанного ID команды с пагинацией для параметров offset и limit... |
| `get_team_member` | Получение участника команды по его email адресу в рамках указанной команды |
| `update_team_member` | Обновление данных участника команды, таких как имя или статус администратора команды, по email адресу в рамках указанной команды... |
| `remove_team_member` | Удаление участника команды из команды по его email адресу |
| `add_team_member` | Добавление нового участника в команду по его email адресу, с опциональным указанием статуса администратора команды... |

## Возможности

- Полное покрытие TeamRetro API с более чем 20 инструментами для управления командами, пользователями, действиями и прочим
- Упрощенная интеграция с AI клиентами через стандартизированные MCP интерфейсы
- Встроенная поддержка пагинации и фильтрации для эффективной обработки данных
- Безопасная обработка аутентификации API и конфигурация окружения
- Исчерпывающая документация и простые варианты настройки

## Переменные окружения

### Обязательные
- `TEAMRETRO_AUTH_TYPE` - Тип аутентификации для TeamRetro API
- `TEAMRETRO_API_KEY` - Ваш API ключ TeamRetro для аутентификации

### Опциональные
- `TEAMRETRO_BASE_URL` - Базовый URL для TeamRetro API (по умолчанию https://api.teamretro.com)

## Ресурсы

- [GitHub Repository](https://github.com/adepanges/teamretro-mcp-server)

## Примечания

Это неофициальный интерфейс к сервисам TeamRetro, разработанный сообществом. Он подключается напрямую к официальному публичному API TeamRetro и поддерживает полное соответствие API. Сервер основан на официальной документации API TeamRetro, и любые изменения в TeamRetro API могут повлиять на функциональность данного MCP сервера.