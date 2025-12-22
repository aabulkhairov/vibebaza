---
title: Fluent-MCP сервер
description: MCP сервер, который предоставляет возможности ServiceNow Fluent SDK в средах разработки с поддержкой ИИ, обеспечивая взаимодействие с командами ServiceNow SDK, спецификациями API, фрагментами кода и ресурсами разработки на естественном языке.
tags:
- DevOps
- Code
- API
- Integration
- Productivity
author: modesty
featured: false
---

MCP сервер, который предоставляет возможности ServiceNow Fluent SDK в средах разработки с поддержкой ИИ, обеспечивая взаимодействие с командами ServiceNow SDK, спецификациями API, фрагментами кода и ресурсами разработки на естественном языке.

## Установка

### NPX

```bash
npx @modelcontextprotocol/inspector npx @modesty/fluent-mcp
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "mcpServers": {
    "fluent-mcp": {
      "command": "npx",
      "args": ["-y", "@modesty/fluent-mcp"],
      "env": {
        "SN_INSTANCE_URL": "https://your-instance.service-now.com",
        "SN_AUTH_TYPE": "oauth"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `sdk_info` | Получить версию SDK, справку или отладочную информацию |
| `manage_fluent_auth` | Управление профилями аутентификации экземпляров |
| `init_fluent_app` | Инициализация или конвертация ServiceNow приложения |
| `build_fluent_app` | Сборка приложения |
| `deploy_fluent_app` | Деплой в экземпляр ServiceNow |
| `fluent_transform` | Конвертация XML в Fluent TypeScript |
| `download_fluent_dependencies` | Скачивание зависимостей и определений типов |
| `download_fluent_app` | Скачивание метаданных с экземпляра |
| `clean_fluent_app` | Очистка выходной директории |
| `pack_fluent_app` | Создание устанавливаемого артефакта |

## Возможности

- Анализ ошибок с помощью ИИ - Интеллектуальная диагностика с определением первопричины, решений и советов по предотвращению
- Полное покрытие SDK - Все команды ServiceNow SDK: auth, init, build, install, dependencies, transform, download, clean, pack
- Богатые ресурсы - Спецификации API, фрагменты кода, инструкции для 35+ типов метаданных
- Аутентификация для разных сред - Поддержка базовой и oauth аутентификации с управлением профилями
- Осведомленность о сессии - Поддерживает контекст рабочей директории между командами
- MCP семплинг - Использует LLM клиента для интеллектуального анализа ошибок при сбоях команд SDK
- MCP выяснение - Интерактивный сбор параметров для сложных рабочих процессов

## Переменные окружения

### Опциональные
- `SN_INSTANCE_URL` - URL экземпляра ServiceNow
- `SN_AUTH_TYPE` - Метод аутентификации: basic или oauth
- `FLUENT_MCP_ENABLE_ERROR_ANALYSIS` - Включить анализ ошибок с помощью ИИ
- `FLUENT_MCP_MIN_ERROR_LENGTH` - Минимальная длина ошибки для анализа

## Примеры использования

```
Create a new Fluent app in ~/projects/time-off-tracker to manage employee PTO requests
```

```
Create a new auth profile for https://dev12345.service-now.com with alias dev-instance
```

```
Create a new Fluent app in ~/projects/asset-tracker for IT asset management
```

```
Show me the business-rule API specification and provide an example snippet
```

```
Build the app with debug output, then deploy to dev-instance
```

## Ресурсы

- [GitHub Repository](https://github.com/modesty/fluent-mcp)

## Примечания

Требует Node.js 22.15.1+ и npm 11.4.1+. Поддерживает 35+ типов метаданных ServiceNow, включая основные типы, типы таблиц и типы ATF (Automated Test Framework). Предоставляет 100+ ресурсов со стандартизированными паттернами URI в соответствии со спецификацией MCP.