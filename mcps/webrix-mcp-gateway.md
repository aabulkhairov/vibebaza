---
title: Webrix MCP Gateway MCP сервер
description: Безопасный открытый OAuth шлюз для аутентификации MCP, который предоставляет
  единый корпоративный интерфейс для подключения, управления и расширения MCP модулей и сервисов.
tags:
- Security
- Integration
- API
- DevOps
- Productivity
author: webrix-ai
featured: false
---

Безопасный открытый OAuth шлюз для аутентификации MCP, который предоставляет единый корпоративный интерфейс для подключения, управления и расширения MCP модулей и сервисов.

## Установка

### NPX (Рекомендуется)

```bash
# По умолчанию (использует ./mcp.json и ./.env)
npx @mcp-s/secure-mcp-gateway

# Кастомные пути конфигурации
npx @mcp-s/secure-mcp-gateway --mcp-config ./custom/mcp.json --envfile ./custom/.env
```

### Из исходного кода

```bash
git clone https://github.com/mcp-s-ai/secure-mcp-gateway.git && cd secure-mcp-gateway
npm install && npm run start
```

### PM2

```bash
pm2 start "npx @mcp-s/secure-mcp-gateway" --name mcp-gateway
```

## Конфигурация

### Файл конфигурации MCP (mcp.json)

```json
{
  "mcpServers": {
    "your-server": {
      "command": "npx",
      "args": ["-y", "@your-mcp-server"],
      "env": {
        "API_KEY": "your-api-key"
      }
    },
    "octocode": {
      "command": "npx",
      "args": ["octocode-mcp"]
    }
  }
}
```

### Конфигурация STDIO

```json
{
  "mcpServers": {
    "mcp-gateway": {
      "command": "npx",
      "args": ["-y", "@mcp-s/mcp"],
      "env": {
        "BASE_URL": "http://localhost:3000"
      }
    }
  }
}
```

### Конфигурация StreamableHTTP

```json
{
  "mcpServers": {
    "mcp-gateway": {
      "url": "http://localhost:3000/mcp"
    }
  }
}
```

## Возможности

- Самохостируемый шлюз - Деплой в собственной инфраструктуре для максимального контроля
- OAuth аутентификация - Безопасная аутентификация с любым OAuth провайдером через Auth.js
- Поддержка TypeScript - Полная типизация для надежной разработки
- Поддержка STDIO подключений - Стандартные input/output MCP серверы
- Поддержка StreamableHTTP подключений - HTTP-стриминг соединения
- Выбор сервера - Подключение к конкретным MCP серверам через параметры запроса
- 80+ OAuth провайдеров - Поддержка Google, Okta, Azure AD, GitHub и других
- Корпоративный интерфейс для подключения, управления и расширения MCP модулей

## Переменные окружения

### Обязательные
- `AUTH_SECRET` - Секрет для подписи/шифрования токенов (сгенерируйте с помощью openssl rand -base64 33)
- `AUTH_GOOGLE_ID` - Google OAuth client ID
- `AUTH_GOOGLE_SECRET` - Google OAuth client secret
- `AUTH_OKTA_ID` - Okta OAuth client ID
- `AUTH_OKTA_SECRET` - Okta OAuth client secret
- `AUTH_OKTA_ISSUER` - Okta issuer URL
- `AUTH_AZURE_AD_ID` - Azure AD client ID
- `AUTH_AZURE_AD_SECRET` - Azure AD client secret

### Опциональные
- `PORT` - Порт сервера
- `BASE_URL` - Базовый URL для шлюза
- `AUTH_PROVIDER` - Название OAuth провайдера
- `TOKEN_EXPIRATION_TIME` - Время истечения токена в миллисекундах
- `DB_PATH` - Путь к файлу базы данных SQLite
- `AUTH_GITHUB_SCOPES` - GitHub OAuth области доступа (например, repo, public_repo, read:user)

## Ресурсы

- [GitHub Repository](https://github.com/webrix-ai/secure-mcp-gateway)

## Примечания

Требует Node.js версии 22 или выше для поддержки SQLite. Поддерживает Claude, Cursor, Windsurf, VSCode, Cline, Highlight AI и Augment Code. Выбор сервера через параметры запроса: http://localhost:3000/mcp?server_name=XXX. Для Cursor с StreamableHTTP убедитесь, что открыто только одно окно во избежание проблем с подключением. Хостируемое решение доступно на webrix.ai с корпоративными возможностями.