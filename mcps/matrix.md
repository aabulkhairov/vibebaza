---
title: Matrix MCP сервер
description: Комплексный сервер Model Context Protocol, который предоставляет безопасный доступ к функциональности Matrix homeserver, позволяя клиентам взаимодействовать с комнатами Matrix, сообщениями, пользователями и администрированием через OAuth 2.0 аутентификацию.
tags:
- Messaging
- API
- Integration
- Security
- Productivity
author: mjknowles
featured: false
install_command: 'claude mcp add --transport http matrix-server http://localhost:3000/mcp
  -H "matrix_user_id:  @user1:matrix.example.com" -H "matrix_homeserver_url: https://localhost:8008"
  -H "matrix_access_token: ${MATRIX_ACCESS_TOKEN}" -H "Authorization: Bearer ${MATRIX_MCP_TOKEN}"'
---

Комплексный сервер Model Context Protocol, который предоставляет безопасный доступ к функциональности Matrix homeserver, позволяя клиентам взаимодействовать с комнатами Matrix, сообщениями, пользователями и администрированием через OAuth 2.0 аутентификацию.

## Установка

### Из исходного кода

```bash
# Clone the repository
git clone <repository-url>
cd matrix-mcp-server

# Install dependencies
npm install

# Build the project
npm run build

# Configure environment
cp .env.example .env
# Edit .env with your settings

# Start the server
npm start
```

### Режим разработки

```bash
# Start with hot reload (OAuth disabled for easier testing)
npm run dev

# Or start with OAuth enabled
ENABLE_OAUTH=true npm run dev
```

## Конфигурация

### VS Code

```json
{
  "servers": {
    "matrix-mcp": {
      "url": "http://localhost:3000/mcp",
      "type": "http",
      "headers": {
        "matrix_access_token": "${input:matrix-access-token}",
        "matrix_user_id": "@<your-matrix-username>:<your-homeserver-domain>",
        "matrix_homeserver_url": "<your-homeserver-url>"
      }
    }
  },
  "inputs": [
    {
      "id": "matrix-access-token",
      "type": "promptString",
      "description": "Your OAuth access token"
    }
  ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list-joined-rooms` | Получить все комнаты, к которым присоединился пользователь |
| `get-room-info` | Получить подробную информацию о комнате |
| `get-room-members` | Показать всех участников комнаты |
| `get-room-messages` | Получить последние сообщения из комнаты |
| `get-messages-by-date` | Фильтровать сообщения по диапазону дат |
| `identify-active-users` | Найти самых активных пользователей по количеству сообщений |
| `get-user-profile` | Получить информацию профиля любого пользователя |
| `get-my-profile` | Получить информацию собственного профиля |
| `get-all-users` | Показать всех пользователей, известных вашему клиенту |
| `search-public-rooms` | Найти публичные комнаты для присоединения |
| `get-notification-counts` | Проверить непрочитанные сообщения и упоминания |
| `get-direct-messages` | Показать все DM беседы |
| `send-message` | Отправить сообщения в комнаты |
| `send-direct-message` | Отправить личные сообщения пользователям |
| `create-room` | Создать новые комнаты Matrix |

## Возможности

- OAuth 2.0 аутентификация с поддержкой обмена токенов
- 15 инструментов Matrix, организованных по функциональным уровням
- Поддержка мультисервера с настраиваемыми endpoints
- Операции в реальном времени с эфемерным управлением клиентами
- Готов к продакшену с комплексной обработкой ошибок
- Богатые ответы с подробными данными Matrix

## Переменные окружения

### Обязательные
- `ENABLE_OAUTH` - Включить OAuth аутентификацию
- `MATRIX_HOMESERVER_URL` - URL Matrix homeserver
- `MATRIX_DOMAIN` - Домен Matrix
- `MATRIX_CLIENT_ID` - ID клиента Matrix
- `MATRIX_CLIENT_SECRET` - Секрет клиента Matrix

### Опциональные
- `PORT` - Порт сервера
- `ENABLE_TOKEN_EXCHANGE` - Обмен OAuth токенов на Matrix токены
- `CORS_ALLOWED_ORIGINS` - Разрешенные origins через запятую (пустое = разрешить все)
- `ENABLE_HTTPS` - Включить HTTPS
- `SSL_KEY_PATH` - Путь к приватному ключу
- `SSL_CERT_PATH` - Путь к сертификату
- `IDP_ISSUER_URL` - URL издателя провайдера идентификации
- `IDP_AUTHORIZATION_URL` - URL авторизации провайдера идентификации

## Ресурсы

- [GitHub Repository](https://github.com/mjknowles/matrix-mcp-server)

## Примечания

Поддерживает как OAuth режим для продакшена, так и режим разработки для тестирования. Инструменты организованы в уровни Tier 0 (только чтение) и Tier 1 (действия). Требует Node.js 20+ и доступ к Matrix homeserver. Заголовок MATRIX_ACCESS_TOKEN опционален, если работает обмен токенов.