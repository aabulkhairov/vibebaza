---
title: Gmail MCP сервер
description: Реализация сервиса Gmail с использованием MCP (Model Context Protocol), которая предоставляет функциональность для отправки, получения и управления электронными письмами через Gmail API со стандартизированной аутентификацией и конфигурацией.
tags:
- Messaging
- API
- Integration
- Productivity
author: gangradeamitesh
featured: false
---

Реализация сервиса Gmail с использованием MCP (Model Context Protocol), которая предоставляет функциональность для отправки, получения и управления электронными письмами через Gmail API со стандартизированной аутентификацией и конфигурацией.

## Установка

### pip

```bash
pip install mcp-google-email
```

## Возможности

- Отправка и получение электронных писем
- Список сообщений с возможностями поиска
- Ответы на существующие сообщения
- Получение сегодняшних сообщений
- Поддержка множественных методов аутентификации (Service Account, OAuth 2.0, Application Default Credentials)
- Конфигурация на основе переменных окружения
- Стандартизированная интеграция с Gmail API
- Обработка электронных писем в реальном времени
- Ведение журналов коммуникаций по электронной почте

## Переменные окружения

### Опциональные
- `GOOGLE_APPLICATION_CREDENTIALS` - Путь к вашему JSON файлу с учетными данными сервисного аккаунта
- `GOOGLE_CREDENTIALS_CONFIG` - JSON строка, содержащая учетные данные сервисного аккаунта

## Примеры использования

```
List unread messages with query filters
```

```
Send emails to recipients with subject and message text
```

```
Get today's messages with result limits
```

```
Reply to specific messages using message ID
```

## Ресурсы

- [GitHub Repository](https://github.com/gangradeamitesh/mcp-google-email)

## Примечания

Требует Python 3.11+ и поддерживает множественные методы аутентификации Gmail API, включая Service Account, OAuth 2.0 и Application Default Credentials. Использует файлы credentials.json и token.json для аутентификации OAuth 2.0.