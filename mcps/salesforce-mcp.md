---
title: Salesforce MCP сервер
description: Реализация сервера Model Context Protocol (MCP) для интеграции с Salesforce, позволяющая языковым моделям взаимодействовать с данными Salesforce через SOQL запросы и SOSL поиск.
tags:
- CRM
- API
- Database
- Integration
- Cloud
author: smn2gnt
featured: true
---

Реализация сервера Model Context Protocol (MCP) для интеграции с Salesforce, позволяющая языковым моделям взаимодействовать с данными Salesforce через SOQL запросы и SOSL поиск.

## Установка

### UVX

```bash
uvx --from mcp-salesforce-connector salesforce
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "salesforce": {
        "command": "uvx",
        "args": [
            "--from",
            "mcp-salesforce-connector",
            "salesforce"
        ],
        "env": {
            "SALESFORCE_ACCESS_TOKEN": "SALESFORCE_ACCESS_TOKEN",
            "SALESFORCE_INSTANCE_URL": "SALESFORCE_INSTANCE_URL",
            "SALESFORCE_DOMAIN": "SALESFORCE_DOMAIN"
            }
        }
    }
}
```

## Возможности

- Выполнение SOQL (Salesforce Object Query Language) запросов
- Выполнение SOSL (Salesforce Object Search Language) поиска
- Получение метаданных для объектов Salesforce, включая имена полей, названия и типы
- Получение, создание, обновление и удаление записей
- Выполнение Tooling API запросов
- Выполнение Apex REST запросов
- Прямые вызовы REST API к Salesforce

## Переменные окружения

### Опциональные
- `SALESFORCE_ACCESS_TOKEN` - OAuth токен доступа для аутентификации в Salesforce (рекомендуемый способ)
- `SALESFORCE_INSTANCE_URL` - URL экземпляра Salesforce для OAuth аутентификации
- `SALESFORCE_DOMAIN` - Установите в 'test' для подключения к sandbox окружению Salesforce, оставьте пустым для продакшена
- `SALESFORCE_USERNAME` - Имя пользователя для устаревшего метода аутентификации (резервный вариант)
- `SALESFORCE_PASSWORD` - Пароль для устаревшего метода аутентификации (резервный вариант)
- `SALESFORCE_SECURITY_TOKEN` - Токен безопасности для устаревшего метода аутентификации (резервный вариант)

## Ресурсы

- [GitHub Repository](https://github.com/smn2gnt/MCP-Salesforce)

## Примечания

Этот сервер поддерживает два способа аутентификации: OAuth (рекомендуемый) с использованием токена доступа и URL экземпляра, или устаревшую аутентификацию через имя пользователя/пароль в качестве резервного варианта. Сервер может подключаться как к продакшн, так и к sandbox окружениям в зависимости от настройки SALESFORCE_DOMAIN.