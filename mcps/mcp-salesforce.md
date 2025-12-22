---
title: mcp-salesforce MCP сервер
description: MCP сервер для базовой интеграции с Salesforce, который позволяет взаимодействовать с функциями Salesforce, такими как отправка электронных писем и развертывание Apex кода через MCP инструменты.
tags:
- CRM
- Integration
- API
- Productivity
- Cloud
author: lciesielski
featured: false
---

MCP сервер для базовой интеграции с Salesforce, который позволяет взаимодействовать с функциями Salesforce, такими как отправка электронных писем и развертывание Apex кода через MCP инструменты.

## Установка

### Из исходного кода

```bash
npm install
# или
yarn install
```

### Запуск

```bash
node server.js
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `email` | Отправка электронных писем через Salesforce |
| `apex_deployment` | Развертывание Apex кода в Salesforce |

## Возможности

- Отправка электронных писем через Salesforce
- Развертывание Apex кода в Salesforce организацию
- Аутентификация через JWT Bearer Flow
- Интеграция с Connected App

## Ресурсы

- [GitHub Repository](https://github.com/lciesielski/mcp-salesforce-example)

## Примечания

Требует создания файла credentials.js с функцией getSalesforceCredentials(), настройки Salesforce Connected App для JWT аутентификации и правильной настройки приватного ключа. В репозитории включен образец файла шаблона claude_desktop_config.json.