---
title: Salesforce MCP Server MCP сервер
description: MCP сервер, который интегрирует Claude с Salesforce, позволяя взаимодействовать на естественном языке для запросов, изменения и управления данными Salesforce, объектами, полями и Apex кодом.
tags:
- CRM
- Database
- API
- Integration
- Code
author: tsmztech
featured: true
---

MCP сервер, который интегрирует Claude с Salesforce, позволяя взаимодействовать на естественном языке для запросов, изменения и управления данными Salesforce, объектами, полями и Apex кодом.

## Установка

### NPM Global

```bash
npm install -g @tsmztech/mcp-server-salesforce
```

### Из исходного кода

```bash
git clone https://github.com/tsmztech/mcp-server-salesforce.git
cd mcp-server-salesforce
npm install
npm run build
```

## Конфигурация

### Claude Desktop - Salesforce CLI

```json
{
  "mcpServers": {
    "salesforce": {
      "command": "npx",
      "args": ["-y", "@tsmztech/mcp-server-salesforce"],
      "env": {
        "SALESFORCE_CONNECTION_TYPE": "Salesforce_CLI"
      }
    }
  }
}
```

### Claude Desktop - Имя пользователя/Пароль

```json
{
  "mcpServers": {
    "salesforce": {
      "command": "npx",
      "args": ["-y", "@tsmztech/mcp-server-salesforce"],
      "env": {
        "SALESFORCE_CONNECTION_TYPE": "User_Password",
        "SALESFORCE_USERNAME": "your_username",
        "SALESFORCE_PASSWORD": "your_password",
        "SALESFORCE_TOKEN": "your_security_token",
        "SALESFORCE_INSTANCE_URL": "org_url"
      }
    }
  }
}
```

### Claude Desktop - OAuth 2.0

```json
{
  "mcpServers": {
    "salesforce": {
      "command": "npx",
      "args": ["-y", "@tsmztech/mcp-server-salesforce"],
      "env": {
        "SALESFORCE_CONNECTION_TYPE": "OAuth_2.0_Client_Credentials",
        "SALESFORCE_CLIENT_ID": "your_client_id",
        "SALESFORCE_CLIENT_SECRET": "your_client_secret",
        "SALESFORCE_INSTANCE_URL": "https://your-domain.my.salesforce.com"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `salesforce_search_objects` | Поиск стандартных и пользовательских объектов по частичному совпадению имен |
| `salesforce_describe_object` | Получение детальной информации о схеме объекта, включая поля, связи и значения списков выбора |
| `salesforce_query_records` | Запрос записей с поддержкой связей и сложными условиями WHERE |
| `salesforce_aggregate_query` | Выполнение агрегированных запросов с функциями GROUP BY, COUNT, SUM, AVG, MIN, MAX |
| `salesforce_dml_records` | Выполнение операций с данными: вставка, обновление, удаление и upsert записей |
| `salesforce_manage_object` | Создание и изменение пользовательских объектов с настройками общего доступа |
| `salesforce_manage_field` | Управление полями объектов, включая создание, изменение и связи |
| `salesforce_manage_field_permissions` | Управление безопасностью на уровне полей и разрешениями для конкретных профилей |
| `salesforce_search_all` | Поиск по нескольким объектам с использованием SOSL с фрагментами полей |
| `salesforce_read_apex` | Чтение Apex классов с исходным кодом и метаданными, поддерживает wildcards |
| `salesforce_write_apex` | Создание и обновление Apex классов с указанием версии API |
| `salesforce_read_apex_trigger` | Чтение Apex триггеров с исходным кодом и метаданными, поддерживает wildcards |
| `salesforce_write_apex_trigger` | Создание и обновление Apex триггеров для конкретных объектов и событий |
| `salesforce_execute_anonymous` | Выполнение анонимного Apex кода и просмотр журналов отладки и результатов выполнения |
| `salesforce_manage_debug_logs` | Включение, отключение и получение журналов отладки для пользователей Salesforce с настраиваемыми уровнями логирования |

## Возможности

- Управление объектами и полями: Создание и изменение пользовательских объектов и полей на естественном языке
- Умный поиск объектов: Поиск объектов Salesforce по частичному совпадению имен
- Детальная информация о схеме: Получение исчерпывающих сведений о полях и связях для любого объекта
- Гибкие запросы данных: Запрос записей с поддержкой связей и сложными фильтрами
- Манипуляция данными: Вставка, обновление, удаление и upsert записей с легкостью
- Поиск по объектам: Поиск по нескольким объектам с использованием SOSL
- Управление Apex кодом: Чтение, создание и обновление Apex классов и триггеров
- Интуитивная обработка ошибок: Понятная обратная связь с деталями ошибок специфичными для Salesforce
- Переключаемая аутентификация: Поддержка нескольких организаций с CLI аутентификацией

## Переменные окружения

### Обязательные
- `SALESFORCE_CONNECTION_TYPE` - Метод аутентификации: Salesforce_CLI, User_Password, или OAuth_2.0_Client_Credentials

### Опциональные
- `SALESFORCE_USERNAME` - Имя пользователя Salesforce для аутентификации User_Password
- `SALESFORCE_PASSWORD` - Пароль Salesforce для аутентификации User_Password
- `SALESFORCE_TOKEN` - Токен безопасности Salesforce для аутентификации User_Password
- `SALESFORCE_INSTANCE_URL` - URL организации Salesforce (опциональный для User_Password, обязательный для OAuth)
- `SALESFORCE_CLIENT_ID` - Client ID для аутентификации OAuth 2.0 Client Credentials
- `SALESFORCE_CLIENT_SECRET` - Client Secret для аутентификации OAuth 2.0 Client Credentials

## Примеры использования

```
Найти все объекты связанные с аккаунтами
```

```
Какие поля доступны в объекте Account?
```

```
Получить все аккаунты созданные в этом месяце
```

```
Подсчитать возможности по стадиям
```

```
Создать объект Customer Feedback
```

## Ресурсы

- [GitHub Repository](https://github.com/tsmztech/mcp-server-salesforce)

## Примечания

Поддерживает три метода аутентификации: Имя пользователя/Пароль, OAuth 2.0 Client Credentials Flow и Salesforce CLI (рекомендуется для разработки). Включает опцию быстрой установки для Claude Desktop с предварительно настроенным файлом расширения .dxt. Безопасность на уровне полей автоматически предоставляется системному администратору по умолчанию, с возможностью указать различные профили.