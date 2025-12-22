---
title: AWS Cognito MCP сервер
description: Реализация сервера Model Context Protocol (MCP), который подключается к
  AWS Cognito для аутентификации и управления пользователями, предоставляя инструменты для
  процессов аутентификации пользователей, включая регистрацию, вход, управление паролями и многое другое.
tags:
- Cloud
- Security
- API
- Integration
author: gitCarrot
featured: false
install_command: claude mcp add "aws-cognito-mcp" npx tsx index.ts
---

Реализация сервера Model Context Protocol (MCP), который подключается к AWS Cognito для аутентификации и управления пользователями, предоставляя инструменты для процессов аутентификации пользователей, включая регистрацию, вход, управление паролями и многое другое.

## Установка

### Из исходного кода

```bash
# Clone the repository
git clone https://github.com/yourusername/mcp-server-aws-cognito.git

# Install dependencies
cd mcp-server-aws-cognito
npm install

# Build the server
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "aws-cognito-mcp-server": {
      "command": "/path/to/mcp-server-aws-cognito/build/index.js",
      "env": {
        "AWS_COGNITO_USER_POOL_ID": "your-user-pool-id",
        "AWS_COGNITO_USER_POOL_CLIENT_ID": "your-app-client-id"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `sign_up` | Зарегистрировать нового пользователя |
| `sign_up_confirm_code_from_email` | Подтвердить аккаунт с помощью кода подтверждения |
| `sign_in` | Аутентифицировать пользователя |
| `sign_out` | Выйти из системы для текущего пользователя |
| `getCurrentUser` | Получить текущего авторизованного пользователя |
| `reset_password_send_code` | Запросить код для сброса пароля |
| `reset_password_veryify_code` | Сбросить пароль с помощью кода подтверждения |
| `change_password` | Изменить пароль для авторизованного пользователя |
| `refresh_session` | Обновить токены аутентификации |
| `update_user_attributes` | Обновить атрибуты профиля пользователя |
| `delete_user` | Удалить текущего авторизованного пользователя |
| `resend_confirmation_code` | Повторно отправить код подтверждения аккаунта |
| `verify_software_token` | Подтвердить TOTP для MFA |

## Возможности

- Регистрация пользователей и подтверждение аккаунта
- Аутентификация пользователей (вход/выход)
- Управление паролями и функционал сброса
- Управление сессиями с обновлением токенов
- Обновление атрибутов профиля пользователя
- Возможности удаления аккаунта
- Поддержка многофакторной аутентификации (MFA) с TOTP
- Повторная отправка кодов подтверждения

## Переменные окружения

### Обязательные
- `AWS_COGNITO_USER_POOL_ID` - Ваш AWS Cognito User Pool ID
- `AWS_COGNITO_USER_POOL_CLIENT_ID` - Ваш AWS Cognito App Client ID

## Ресурсы

- [GitHub Repository](https://github.com/gitCarrot/mcp-server-aws-cognito)

## Примечания

Требует аккаунт AWS с настроенным Cognito User Pool и Node.js 18 или выше. Файл .env нужен только при использовании Claude Code, но не Claude Desktop. Режим разработки с автоматической пересборкой доступен через 'npm run watch'. MCP Inspector доступен для отладки с помощью 'npm run inspector'.