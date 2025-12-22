---
title: Google Ads MCP сервер
description: FastMCP-powered Model Context Protocol сервер для интеграции с Google Ads API с автоматической OAuth 2.0 аутентификацией, позволяющий выполнять GAQL запросы и исследовать ключевые слова.
tags:
- API
- Analytics
- Integration
- Cloud
- Productivity
author: gomarble-ai
featured: false
---

FastMCP-powered Model Context Protocol сервер для интеграции с Google Ads API с автоматической OAuth 2.0 аутентификацией, позволяющий выполнять GAQL запросы и исследовать ключевые слова.

## Установка

### Из исходников

```bash
# Clone the repository
git clone https://github.com/yourusername/google-ads-mcp-server.git
cd google-ads-mcp-server

# Create virtual environment (recommended)
python3 -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### HTTP режим

```bash
# Start server in HTTP mode
python3 server.py --http
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "google-ads": {
      "command": "/full/path/to/your/project/.venv/bin/python",
      "args": [
        "/full/path/to/your/project/server.py"
      ]
    }
  }
}
```

### Конфигурация HTTP режима

```json
{
  "mcpServers": {
    "google-ads": {
      "url": "http://127.0.0.1:8000/mcp"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `list_accounts` | Получить список всех доступных Google Ads аккаунтов |
| `run_gaql` | Выполнить GAQL запросы с кастомным форматированием |
| `run_keyword_planner` | Генерировать идеи ключевых слов с метриками |

## Возможности

- Автоматическая OAuth 2.0 аутентификация с одноразовой настройкой в браузере
- Умное управление токенами с автоматическим обновлением
- Выполнение GAQL (Google Ads Query Language) запросов
- Управление аккаунтами и получение их списка
- Исследование ключевых слов с данными о поисковых запросах
- Построен на FastMCP фреймворке
- Готовая интеграция с Claude Desktop
- Безопасное локальное хранение токенов

## Переменные окружения

### Обязательные
- `GOOGLE_ADS_DEVELOPER_TOKEN` - Google Ads API Developer токен
- `GOOGLE_ADS_OAUTH_CONFIG_PATH` - Путь к JSON файлу OAuth учетных данных, скачанному из Google Cloud

### Опциональные
- `GOOGLE_ADS_LOGIN_CUSTOMER_ID` - Конфигурация менеджерского аккаунта для управления несколькими аккаунтами под MCC

## Примеры использования

```
List all my Google Ads accounts
```

```
Show me campaign performance for account 1234567890 in the last 30 days
```

```
Generate keyword ideas for 'digital marketing' using account 1234567890
```

```
Get conversion data for all campaigns in the last week
```

```
Which campaigns have the highest cost per conversion?
```

## Ресурсы

- [GitHub Repository](https://github.com/gomarble-ai/google-ads-mcp-server)

## Примечания

Требуется аккаунт Google Cloud Platform, Google Ads аккаунт с доступом к API и одобренный developer токен. Включает подробное руководство по настройке OAuth 2.0 учетных данных и конфигурации Google Ads API. Установщик в один клик доступен на https://gomarble.ai/mcp