---
title: Keycloak MCP сервер
description: MCP сервер для администрирования Keycloak, предоставляющий инструменты для управления пользователями и реалмами через взаимодействие на естественном языке.
tags:
- Security
- DevOps
- API
- Integration
author: ChristophEnglisch
featured: false
install_command: npx -y @smithery/cli install keycloak-model-context-protocol --client
  claude
---

MCP сервер для администрирования Keycloak, предоставляющий инструменты для управления пользователями и реалмами через взаимодействие на естественном языке.

## Установка

### Smithery

```bash
npx -y @smithery/cli install keycloak-model-context-protocol --client claude
```

### NPX

```bash
npx -y keycloak-model-context-protocol
```

### NPM Global

```bash
npm install -g keycloak-model-context-protocol
```

### Из исходников

```bash
git clone <repository-url>
cd keycloak-model-context-protocol
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPM пакет)

```json
{
  "mcpServers": {
    "keycloak": {
      "command": "npx",
      "args": ["-y", "keycloak-model-context-protocol"],
      "env": {
        "KEYCLOAK_URL": "http://localhost:8080",
        "KEYCLOAK_ADMIN": "admin",
        "KEYCLOAK_ADMIN_PASSWORD": "admin"
      }
    }
  }
}
```

### Claude Desktop (локальная разработка)

```json
{
  "mcpServers": {
    "keycloak": {
      "command": "node",
      "args": ["path/to/dist/index.js"],
      "env": {
        "KEYCLOAK_URL": "http://localhost:8080",
        "KEYCLOAK_ADMIN": "admin",
        "KEYCLOAK_ADMIN_PASSWORD": "admin"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create-user` | Создает нового пользователя в указанном реалме с именем пользователя, email, именем и фамилией |
| `delete-user` | Удаляет пользователя из указанного реалма по его ID |
| `list-realms` | Отображает список всех доступных реалмов в экземпляре Keycloak |
| `list-users` | Отображает список всех пользователей в указанном реалме |

## Возможности

- Создание новых пользователей в определенных реалмах
- Удаление пользователей из реалмов
- Просмотр доступных реалмов
- Просмотр пользователей в определенных реалмах

## Переменные окружения

### Обязательные
- `KEYCLOAK_URL` - URL экземпляра Keycloak
- `KEYCLOAK_ADMIN` - Имя пользователя администратора для аутентификации в Keycloak
- `KEYCLOAK_ADMIN_PASSWORD` - Пароль администратора для аутентификации в Keycloak

## Ресурсы

- [GitHub Repository](https://github.com/ChristophEnglisch/keycloak-model-context-protocol)

## Примечания

Требует Node.js 18 или выше и работающий экземпляр Keycloak. Проект автоматически публикуется в NPM через GitHub Actions. Для тестирования используйте MCP Inspector с командой: npx -y @modelcontextprotocol/inspector npx -y keycloak-model-context-protocol