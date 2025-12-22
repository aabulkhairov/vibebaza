---
title: Webflow MCP сервер
description: Этот MCP сервер позволяет Claude взаимодействовать с API Webflow для получения информации о сайтах и управления сайтами Webflow.
tags:
- API
- Web
- CMS
- Integration
- Productivity
author: Community
featured: false
---

Этот MCP сервер позволяет Claude взаимодействовать с API Webflow для получения информации о сайтах и управления сайтами Webflow.

## Установка

### NPM Install

```bash
npm install
```

### Smithery

```bash
npx -y @smithery/cli install @kapilduraphe/webflow-mcp-server --client claude
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "webflow": {
            "command": "node",
            "args": [
                "/ABSOLUTE/PATH/TO/YOUR/build/index.js"
            ],
            "env": {
                "WEBFLOW_API_TOKEN": "your-api-token"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_sites` | Получает список всех сайтов Webflow, доступных аутентифицированному пользователю, с подробной информацией... |
| `get_site` | Получает подробную информацию о конкретном сайте Webflow по ID, возвращая те же детальные данные... |

## Возможности

- Доступ ко всем сайтам Webflow для аутентифицированного пользователя
- Получение подробной информации о сайте, включая метаданные
- Получение конфигурации пользовательских доменов
- Доступ к настройкам локализации (основные и дополнительные локали)
- Просмотр настроек сбора данных
- Запрос конкретных сайтов по ID
- Комплексная обработка ошибок для проблем с API

## Переменные окружения

### Обязательные
- `WEBFLOW_API_TOKEN` - токен Webflow API (токен сайта или OAuth Access Token) для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/kapilduraphe/webflow-mcp-server)

## Примечания

Требует Node.js версии 16 или выше и аккаунт Webflow. API токен можно сгенерировать в настройках сайта в разделе Apps & Integrations панели управления Webflow. Включает комплексные определения типов TypeScript для ответов API и подробное руководство по устранению неполадок.