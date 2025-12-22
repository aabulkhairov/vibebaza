---
title: GitHub GraphQL MCP сервер
description: MCP сервер, который предоставляет доступ к GitHub GraphQL API, позволяя выполнять произвольные GraphQL запросы и мутации для получения данных репозиториев, информации о пользователях и других ресурсов GitHub.
tags:
- API
- Code
- DevOps
- Integration
- Analytics
author: QuentinCody
featured: false
---

MCP сервер, который предоставляет доступ к GitHub GraphQL API, позволяя выполнять произвольные GraphQL запросы и мутации для получения данных репозиториев, информации о пользователях и других ресурсов GitHub.

## Установка

### Из исходников

```bash
# Clone repository
# Set up virtual environment:
python3 -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
# Install dependencies:
pip install -r requirements.txt
```

### Запуск сервера

```bash
# Activate virtual environment
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
# Run with GitHub token
GITHUB_TOKEN=your_github_token_here python github_graphql_mcp_server.py
```

## Конфигурация

### Claude Desktop

```json
{
  "github-graphql": {
    "command": "/absolute/path/to/your/.venv/bin/python",
    "args": [
        "/absolute/path/to/github_graphql_mcp_server.py"
    ],
    "options": {
        "cwd": "/absolute/path/to/repository"
    },
    "env": {
        "GITHUB_TOKEN": "your_github_token_here"
    }
  }
}
```

## Возможности

- Выполнение любых GraphQL запросов к GitHub API
- Комплексная обработка и отчётность по ошибкам
- Подробная документация с примерами запросов
- Поддержка переменных в GraphQL операциях

## Переменные окружения

### Обязательные
- `GITHUB_TOKEN` - GitHub Personal Access Token для аутентификации в API

## Примеры использования

```
Получение информации о репозитории, включая название, описание, звёзды и данные владельца
```

```
Поиск репозиториев по языку программирования и количеству звёзд
```

```
Получение информации о пользователе, включая биографию, подписчиков и топовые репозитории
```

```
Запрос количества звёзд репозитория и дат создания
```

```
Поиск Python репозиториев с более чем 1000 звёзд
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/github-graphql-mcp-server)

## Примечания

Требуется Python 3.10 или выше. Обратите внимание на лимиты GitHub API: 5,000 запросов в час для аутентифицированных запросов, 60 для неаутентифицированных. Частые проблемы включают неправильные пути к Python в конфиге Claude Desktop и отсутствие активации виртуального окружения.