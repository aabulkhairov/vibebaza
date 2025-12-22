---
title: Neo4j MCP сервер
description: MCP сервер, который обеспечивает интеграцию между графовой базой данных Neo4j
  и Claude Desktop, позволяя выполнять операции с графовой базой данных через естественное языковое взаимодействие.
tags:
- Database
- Analytics
- Integration
- Storage
author: Community
featured: false
---

MCP сервер, который обеспечивает интеграцию между графовой базой данных Neo4j и Claude Desktop, позволяя выполнять операции с графовой базой данных через естественное языковое взаимодействие.

## Установка

### NPX Direct

```bash
npx @alanse/mcp-neo4j
```

### Smithery

```bash
npx -y @smithery/cli install @alanse/mcp-neo4j-server --client claude
```

### Из исходного кода

```bash
git clone https://github.com/da-okazaki/mcp-neo4j-server.git
cd mcp-neo4j-server
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "neo4j": {
      "command": "npx",
      "args": ["@alanse/mcp-neo4j-server"],
      "env": {
        "NEO4J_URI": "bolt://localhost:7687",
        "NEO4J_USERNAME": "neo4j",
        "NEO4J_PASSWORD": "your-password",
        "NEO4J_DATABASE": "neo4j"
      }
    }
  }
}
```

### Neo4j Enterprise Database

```json
{
  "env": {
    "NEO4J_URI": "bolt://localhost:7687",
    "NEO4J_USERNAME": "neo4j",
    "NEO4J_PASSWORD": "your-password",
    "NEO4J_DATABASE": "myCustomDatabase"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `execute_query` | Выполнение Cypher запросов к базе данных Neo4j - поддерживает все типы Cypher запросов (READ, CREATE... |
| `create_node` | Создание новой вершины в графовой базе данных с указанными метками и свойствами, поддерживая все Neo4... |
| `create_relationship` | Создание связи между двумя существующими вершинами с определенным типом, направлением и свойствами |

## Возможности

- Поддержка Neo4j Enterprise Edition с подключениями к конкретным базам данных
- Выполнение всех типов Cypher запросов (READ, CREATE, UPDATE, DELETE)
- Создание вершин с метками и свойствами
- Создание связей между существующими вершинами
- Поддержка параметров для предотвращения атак внедрения кода
- Структурированный формат результатов запросов
- Поддержка всех типов данных Neo4j

## Переменные окружения

### Обязательные
- `NEO4J_PASSWORD` - Пароль Neo4j

### Опциональные
- `NEO4J_URI` - URI базы данных Neo4j (по умолчанию: bolt://localhost:7687)
- `NEO4J_USERNAME` - Имя пользователя Neo4j (по умолчанию: neo4j)
- `NEO4J_DATABASE` - Имя базы данных Neo4j (по умолчанию: neo4j) - Используйте это для подключения к конкретной базе данных в Neo4j Enterprise

## Примеры использования

```
Покажи всех сотрудников из отдела продаж
```

```
Найди топ-5 самых старых клиентов
```

```
Кто купил больше 3 товаров за последний месяц?
```

```
Добавь нового человека по имени Иван Иванов, которому 30 лет
```

```
Создай продукт под названием 'Премиум кофе' с ценой $24.99
```

## Ресурсы

- [GitHub Repository](https://github.com/da-okazaki/mcp-neo4j-server)

## Примечания

Поддерживает Neo4j Enterprise Edition с подключениями к нескольким базам данных. Включает комплексные примеры естественно-языкового взаимодействия для запросов, создания данных и установления связей в графовой базе данных.