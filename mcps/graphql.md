---
title: GraphQL MCP сервер
description: MCP сервер, который автоматически предоставляет каждый GraphQL запрос как отдельный MCP инструмент, обеспечивая бесшовное взаимодействие с GraphQL API через динамическую генерацию схемы и настраиваемую аутентификацию.
tags:
- API
- Database
- Integration
- Analytics
- Code
author: Community
featured: false
---

MCP сервер, который автоматически предоставляет каждый GraphQL запрос как отдельный MCP инструмент, обеспечивая бесшовное взаимодействие с GraphQL API через динамическую генерацию схемы и настраиваемую аутентификацию.

## Установка

### uvx (рекомендуется)

```bash
uvx mcp-graphql --api-url="https://api.example.com/graphql" --auth-token="your-token"
```

### pip

```bash
pip install mcp-graphql
```

### Из исходного кода

```bash
git clone https://github.com/your-username/mcp_graphql.git
cd mcp_graphql
pip install .
```

## Конфигурация

### Claude Desktop (uvx)

```json
"mcpServers": {
  "graphql": {
    "command": "uvx",
    "args": ["mcp-graphql", "--api-url", "https://api.example.com/graphql"]
  }
}
```

### Claude Desktop (Docker)

```json
"mcpServers": {
  "graphql": {
    "command": "docker",
    "args": ["run", "-i", "--rm", "mcp/graphql", "--api-url", "https://api.example.com/graphql"]
  }
}
```

### Claude Desktop (pip)

```json
"mcpServers": {
  "graphql": {
    "command": "python",
    "args": ["-m", "mcp_graphql", "--api-url", "https://api.example.com/graphql"]
  }
}
```

## Возможности

- Каждый GraphQL запрос предоставляется как отдельный MCP инструмент
- Параметры инструментов автоматически соответствуют параметрам GraphQL запросов
- JSON схема для входных данных инструментов динамически генерируется из параметров GraphQL запросов
- Не требует определения схемы - просто укажите URL API и учетные данные
- Поддерживает GraphQL запросы (поддержка мутаций планируется)
- Настраиваемая аутентификация (Bearer, Basic, пользовательские заголовки)
- Автоматическая обработка сложных GraphQL типов
- Автоматическая генерация запросов через интроспекцию GraphQL схемы
- Настраиваемая максимальная глубина для генерации запросов
- Поддержка предопределенных запросов через файл или строковый ввод

## Переменные окружения

### Опциональные
- `MCP_AUTH_TOKEN` - Токен аутентификации для доступа к GraphQL API

## Примеры использования

```
Запрос пользовательских данных из GraphQL API
```

```
Получение постов и статей из системы управления контентом
```

```
Извлечение данных из GitHub GraphQL API
```

```
Доступ к каталогам товаров электронной коммерции через GraphQL
```

## Ресурсы

- [GitHub Repository](https://github.com/drestrepom/mcp_graphql)

## Примечания

Требует Python 3.11 или выше. Сервер автоматически выполняет интроспекцию GraphQL API и динамически создает инструменты. При использовании автоматически генерируемых запросов учитывайте ограничения по глубине, чтобы не перегружать контекстное окно LLM. Для продакшн-использования рекомендуется определять конкретные запросы через --queries-file или --queries для лучшего контроля и производительности.