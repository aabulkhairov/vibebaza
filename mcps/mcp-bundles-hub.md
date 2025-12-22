---
title: MCP Bundles Hub MCP сервер
description: Унифицированный MCP сервер, который предоставляет доступ к более чем 500 интеграциям провайдеров через бандлы, позволяя AI-ассистентам выполнять инструменты из GitHub, Slack, Notion, Google Drive, Salesforce, Stripe и других сервисов через единую точку доступа.
tags:
- Integration
- API
- Productivity
- Cloud
- DevOps
author: thinkchainai
featured: false
---

Унифицированный MCP сервер, который предоставляет доступ к более чем 500 интеграциям провайдеров через бандлы, позволяя AI-ассистентам выполнять инструменты из GitHub, Slack, Notion, Google Drive, Salesforce, Stripe и других сервисов через единую точку доступа.

## Установка

### Прямая загрузка

```bash
Download hub.mcpb from: https://github.com/thinkchainai/mcpbundles/releases/download/hub-v1.0.0%2Bbuild.8da55d55/hub.mcpb
```

### Установка в один клик в Cursor

```bash
Add Server URL: https://github.com/thinkchainai/mcpbundles/releases/download/hub-v1.0.0%2Bbuild.8da55d55/hub.mcpb
```

### NPX

```bash
npx -y mcp-remote@latest https://mcp.mcpbundles.com/hub/ --header "Authorization:Bearer ${ACCESS_TOKEN}"
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "mcpbundles-hub": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote@latest",
        "https://mcp.mcpbundles.com/hub/",
        "--header",
        "Authorization:Bearer ${ACCESS_TOKEN}"
      ],
      "env": {
        "ACCESS_TOKEN": "your_access_token_here"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "mcpbundles-hub": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote@latest",
        "https://mcp.mcpbundles.com/hub/",
        "--header",
        "Authorization:Bearer ${ACCESS_TOKEN}"
      ],
      "env": {
        "ACCESS_TOKEN": "your_access_token_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `mcpbundles_hub_list_bundles` | Получить список всех ваших бандлов |
| `mcpbundles_hub_get_bundle` | Получить детали конкретного бандла |
| `mcpbundles_hub_create_bundle` | Создать новый бандл |
| `mcpbundles_hub_update_bundle` | Обновить конфигурацию бандла |
| `mcpbundles_hub_delete_bundle` | Удалить бандл |
| `mcpbundles_hub_list_credentials` | Получить список ваших учетных данных провайдеров |
| `mcpbundles_hub_add_credential` | Добавить новые учетные данные провайдера |
| `mcpbundles_hub_update_credential` | Обновить существующие учетные данные |
| `mcpbundles_hub_remove_credential` | Удалить учетные данные |
| `mcpbundles_hub_search_providers` | Поиск доступных провайдеров |
| `mcpbundles_hub_get_provider_info` | Получить подробную информацию о провайдере |
| `mcpbundles_hub_list_provider_tools` | Получить список инструментов для конкретного провайдера |
| `mcpbundles_hub_get_account_info` | Просмотреть детали вашего аккаунта |
| `mcpbundles_hub_get_usage_stats` | Проверить статистику использования API |

## Возможности

- OAuth и API Key аутентификация для безопасного доступа
- Унифицированный доступ для выполнения инструментов из нескольких бандлов через одну точку доступа
- Обнаружение инструментов для поиска и получения списка всех доступных инструментов
- Выполнение с учетом бандлов и автоматическим управлением учетными данными
- Проверки готовности для верификации статуса конфигурации
- Более 500 интеграций провайдеров, включая GitHub, Slack, Notion, Google Drive, Salesforce, Stripe

## Переменные окружения

### Обязательные
- `ACCESS_TOKEN` - токен доступа MCPBundles для аутентификации

## Примеры использования

```
Используй инструмент GitHub create_issue из моего dev-tools бандла
```

```
Выполни инструмент slack_send_message чтобы отправить обновление
```

```
Запусти инструмент notion_create_page с заголовком 'Meeting Notes'
```

```
Какие инструменты доступны в моем marketing бандле?
```

```
Покажи все GitHub инструменты, к которым у меня есть доступ
```

## Ресурсы

- [GitHub Repository](https://github.com/thinkchainai/mcpbundles)

## Примечания

Требуется аккаунт MCPBundles (бесплатно на mcpbundles.com). Hub MCP сервер предназначен для управления вашим аккаунтом и бандлами - каждый отдельный бандл получает свой собственный URL MCP сервера для выполнения инструментов. Поддерживает как OAuth (рекомендуется), так и API key аутентификацию. Формат файлов .mcpb предоставляет предварительно сконфигурированные пакеты MCP серверов для простой установки.