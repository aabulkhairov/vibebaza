---
title: Ticketmaster MCP сервер
description: Сервер Model Context Protocol, который предоставляет инструменты для поиска событий, площадок и развлечений через Ticketmaster Discovery API с гибкой фильтрацией и различными форматами вывода.
tags:
- API
- Search
- Integration
- Media
author: delorenj
featured: false
install_command: npx -y @smithery/cli install mcp-server-ticketmaster --client claude
---

Сервер Model Context Protocol, который предоставляет инструменты для поиска событий, площадок и развлечений через Ticketmaster Discovery API с гибкой фильтрацией и различными форматами вывода.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-server-ticketmaster --client claude
```

### Ручная установка

```bash
npx -y install @delorenj/mcp-server-ticketmaster
```

## Конфигурация

### Настройки MCP

```json
{
  "mcpServers": {
    "ticketmaster": {
      "command": "npx",
      "args": ["-y", "@delorenj/mcp-server-ticketmaster"],
      "env": {
        "TICKETMASTER_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_ticketmaster` | Поиск событий, площадок и развлечений с гибкими опциями фильтрации, включая поиск по ключевым словам... |

## Возможности

- Поиск событий, площадок и развлечений с гибкой фильтрацией
- Возможности поиска по ключевым словам
- Фильтрация по диапазону дат для событий
- Поиск по местоположению (город, штат, страна)
- Поиск по конкретным площадкам и развлечениям
- Фильтрация по классификациям/категориям событий
- Структурированный вывод данных в JSON для программного использования
- Человекочитаемый текстовый вывод для прямого потребления
- Comprehensive данные, включая названия, ID, даты, время, диапазоны цен, URL, изображения, местоположения, адреса и классификации

## Переменные окружения

### Обязательные
- `TICKETMASTER_API_KEY` - API ключ из портала разработчиков Ticketmaster для доступа к Discovery API

## Примеры использования

```
Search for concerts in New York during February 2025
```

```
Find events by keyword with date range filtering
```

```
Search for venues in specific cities
```

```
Look up attractions by classification
```

## Ресурсы

- [GitHub Repository](https://github.com/delorenj/mcp-server-ticketmaster)

## Примечания

Требует API ключ Ticketmaster с https://developer.ticketmaster.com/. Сервер поддерживает как JSON, так и текстовые форматы вывода, с различными опциональными параметрами для уточненного поиска, включая ID площадок, ID развлечений и названия классификаций.