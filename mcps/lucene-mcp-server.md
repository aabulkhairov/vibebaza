---
title: lucene-mcp-server MCP сервер
description: Java-based MCP сервер, который предоставляет эффективные возможности поиска и извлечения документов с использованием Apache Lucene для полнотекстового индексирования и поиска, построенный на Spring Boot.
tags:
- Search
- Database
- API
- Analytics
- Storage
author: Community
featured: false
---

Java-based MCP сервер, который предоставляет эффективные возможности поиска и извлечения документов с использованием Apache Lucene для полнотекстового индексирования и поиска, построенный на Spring Boot.

## Установка

### Из исходного кода

```bash
git clone https://github.com/your-username/mcp-lucene-server.git
cd mcp-lucene-server
mvn clean install
java -jar target/mcp-lucene-server-0.0.1-SNAPSHOT.jar
```

### Docker

```bash
docker build -t mcp-lucene-server .
docker run -p 8080:8080 mcp-lucene-server
```

### Spring Boot

```bash
mvn spring-boot:run
```

### MCP Shim

```bash
cd mcp-shim
npm install
LUCENE_BASE_URL=http://localhost:8080/mcp/v1 npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "lucene": {
      "command": "/opt/homebrew/bin/node",
      "args": [".../MCP-Lucene-Server/mcp-shim/server.js"],
      "env": {
        "LUCENE_BASE_URL": "http://localhost:8080/mcp/v1",
        "MCP_FORCE_TEXT": "1"
      }
    }
  }
}
```

### Claude Desktop с обёрточным скриптом

```json
{
  "mcpServers": {
    "lucene": {
      "command": ".../MCP-Lucene-Server/mcp-shim/run-shim.sh",
      "env": {
        "LUCENE_BASE_URL": "http://localhost:8080/mcp/v1",
        "MCP_FORCE_TEXT": "1"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `lucene_status` | Получить статус сервера/индекса |
| `lucene_upsert` | Добавить или обновить документы |
| `lucene_query` | Запросить документы (с опциональными фильтрами метаданных) |
| `lucene_delete` | Удалить по ID |
| `lucene_list` | Список документов с пагинацией |

## Возможности

- MCP совместимость: Реализует основной Model Context Protocol
- На основе Lucene: Использует Apache Lucene для полнотекстового поиска и индексирования
- RESTful API: Предоставляет RESTful API для взаимодействия с сервером
- Управление документами: Добавление, обновление, удаление и просмотр списка документов в Lucene индексе
- Сложные запросы: Поддерживает сложные запросы с использованием синтаксиса запросов Lucene
- Фильтрация: Фильтрация запросов на основе метаданных документов
- Spring Boot: Построен на Spring Boot для простой настройки и деплоя
- Докеризация: Включает инструкции для контейнеризации приложения с использованием Docker

## Переменные окружения

### Обязательные
- `LUCENE_BASE_URL` - Базовый URL для API сервера Lucene

### Опциональные
- `MCP_FORCE_TEXT` - Принудительный текстовый вывод, если клиент не может отрендерить JSON выводы инструментов

## Примеры использования

```
Run lucene_status
```

```
Run lucene_list with: { "limit": 10, "offset": 0 }
```

```
Run lucene_upsert with: {"documents":[{"id":"doc-1","text":"hello world","metadata":{"lang":"en"}}]}
```

```
Run lucene_query with: {"queries":[{"query":"hello","top_k":5}]}
```

```
Run lucene_delete with: { "ids": ["doc-1"] }
```

## Ресурсы

- [GitHub Repository](https://github.com/VivekKumarNeu/MCP-Lucene-Server)

## Примечания

Требует Java 11+, Maven 3.6.0+ и опционально Docker. Сервер работает на порту 8080 по умолчанию. Конфигурация может быть настроена с использованием свойств приложения Spring Boot, включая server.port и lucene.index.path. MCP shim позволяет интеграцию с Claude Desktop через STDIO.