---
title: Catalysis Hub MCP сервер
description: Model Context Protocol сервер, который предоставляет программный доступ к GraphQL API Catalysis Hub, позволяя AI агентам запрашивать данные каталитических исследований, включая реакции, материалы, публикации и данные поверхностных реакций.
tags:
- API
- Database
- Search
- Analytics
author: QuentinCody
featured: false
---

Model Context Protocol сервер, который предоставляет программный доступ к GraphQL API Catalysis Hub, позволяя AI агентам запрашивать данные каталитических исследований, включая реакции, материалы, публикации и данные поверхностных реакций.

## Установка

### Из исходного кода

```bash
git clone <repository_url>
cd catalysishub-mcp-server
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop

```json
{
  "command": "/Users/quentincody/.env/bin/python3",
  "args": ["/Users/quentincody/catalysishub-mcp-server/catalysishub_mcp_server.py"],
  "options": {
    "cwd": "/Users/quentincody/catalysishub-mcp-server"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `catalysishub_graphql` | Выполняет GraphQL запросы к API Catalysis Hub для получения данных каталитических исследований |

## Возможности

- Прямой доступ к GraphQL для выполнения любых валидных запросов к API Catalysis Hub
- Доступ к данным каталитических реакций (уравнения, условия, катализаторы)
- Данные материальных систем (структуры, свойства, дескрипторы)
- Информация о научных публикациях (названия, DOI, авторы)
- Данные поверхностных реакций (энергии адсорбции, центры связывания)
- Гибкая поддержка запросов с параметризацией переменных
- Надежная обработка ошибок для подключения к API и выполнения запросов

## Примеры использования

```
Get the first 5 catalytic reactions with their equations and temperatures
```

```
Find material systems by ID and get their related reactions
```

```
Search for publications by author or DOI
```

```
Query surface reaction data with adsorption energies
```

```
Execute complex GraphQL queries with fragments and variables
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/catalysishub-mcp-server)

## Примечания

Требует сетевого подключения к api.catalysis-hub.org. Использует httpx для асинхронных HTTP запросов. Доступен под лицензией MIT с требованием академического цитирования для исследовательского использования. Включает GraphQL Playground для тестирования запросов по адресу https://www.catalysis-hub.org/api/graphql