---
title: Postman API MCP сервер
description: Postman MCP сервер соединяет Postman с инструментами ИИ, предоставляя AI-агентам и ассистентам возможность получать доступ к рабочим пространствам, управлять коллекциями и окружениями, оценивать API и автоматизировать рабочие процессы через взаимодействие на естественном языке.
tags:
- API
- Productivity
- DevOps
- Integration
- Code
author: postmanlabs
featured: true
install_command: claude mcp add postman --env POSTMAN_API_KEY=YOUR_KEY -- npx @postman/postman-mcp-server@latest
---

Postman MCP сервер соединяет Postman с инструментами ИИ, предоставляя AI-агентам и ассистентам возможность получать доступ к рабочим пространствам, управлять коллекциями и окружениями, оценивать API и автоматизировать рабочие процессы через взаимодействие на естественном языке.

## Установка

### NPX (минимальная)

```bash
npx @postman/postman-mcp-server
```

### NPX (полная)

```bash
npx @postman/postman-mcp-server --full
```

### NPX (код)

```bash
npx @postman/postman-mcp-server --code
```

### Docker

```bash
See DOCKER.md for setup and installation
```

### Gemini CLI

```bash
gemini extensions install https://github.com/postmanlabs/postman-mcp-server
```

## Конфигурация

### Ручная настройка VS Code

```json
{
    "servers": {
        "postman-api-http-server": {
            "type": "http",
            "url": "https://mcp.postman.com/{minimal OR code OR mcp}",
            "headers": {
                "Authorization": "Bearer ${input:postman-api-key}"
            }
        }
    },
    "inputs": [
        {
            "id": "postman-api-key",
            "type": "promptString",
            "description": "Enter your Postman API key"
        }
    ]
}
```

### Конфигурация локального сервера

```json
{
    "servers": {
        "postman-api-mcp": {
            "type": "stdio",
            "command": "npx",
            "args": [
                "@postman/postman-mcp-server",
                "--full",
                "--code",
                "--region us"
            ],
            "env": {
                "POSTMAN_API_KEY": "${input:postman-api-key}"
            }
        }
    },
    "inputs": [
        {
            "id": "postman-api-key",
            "type": "promptString",
            "description": "Enter your Postman API key"
        }
    ]
}
```

## Возможности

- Тестирование API - Непрерывное тестирование вашего API с использованием коллекций Postman
- Синхронизация кода - Легкая синхронизация кода с коллекциями и спецификациями Postman
- Управление коллекциями - Создание и тегирование коллекций, обновление документации, добавление комментариев
- Управление рабочими пространствами и окружениями - Создание рабочих пространств и окружений, управление переменными окружения
- Автоматическое создание спецификаций - Создание спецификаций из вашего кода и их использование для генерации коллекций
- Генерация клиентского кода - Генерация готового к продакшену клиентского кода, который потребляет API согласно лучшим практикам
- Три конфигурации инструментов: минимальная (37 основных инструментов), полная (100+ инструментов), код (генерация клиентского кода API)
- Поддержка региона EU с выделенными эндпоинтами
- Опции развертывания удаленного и локального сервера

## Переменные окружения

### Обязательные
- `POSTMAN_API_KEY` - Ваш API ключ Postman для аутентификации

### Опциональные
- `POSTMAN_API_BASE_URL` - Базовый URL для Postman API (может быть установлен вместо использования флага --region)

## Ресурсы

- [GitHub Repository](https://github.com/postmanlabs/postman-api-mcp)

## Примечания

Миграция с v1.x на v2.x требует обновления названий инструментов с kebab-case на camelCase (например, create-collection → createCollection). Сервер поддерживает удаленное развертывание через потоковый HTTP на mcp.postman.com с различными эндпоинтами для минимальной, код и полной конфигураций. Доступна поддержка региона EU на mcp.eu.postman.com. Для начала работы требуется действующий API ключ Postman.