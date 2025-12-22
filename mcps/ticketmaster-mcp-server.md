---
title: Ticketmaster MCP сервер
description: MCP сервер, который предоставляет инструменты для поиска мероприятий, площадок и достопримечательностей через Ticketmaster Discovery API, позволяя AI-ассистентам получать доступ к обширной базе данных развлекательных событий и площадок Ticketmaster.
tags:
- API
- Search
- Integration
- Analytics
- Productivity
author: mochow13
featured: false
---

MCP сервер, который предоставляет инструменты для поиска мероприятий, площадок и достопримечательностей через Ticketmaster Discovery API, позволяя AI-ассистентам получать доступ к обширной базе данных развлекательных событий и площадок Ticketmaster.

## Установка

### Из исходного кода

```bash
git clone https://github.com/mochow13/ticketmaster-mcp-server.git
cd ticketmaster-mcp-server/server
npm install
npm run build
node build/index.js
```

### Docker

```bash
docker build -t ticketmaster-mcp-server .
docker run -p 3000:3000 ticketmaster-mcp-server
```

## Конфигурация

### Конфигурация Smithery

```json
startCommand:
  type: http
  configSchema:
    type: object
    properties: {}
  exampleConfig: {}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_ticketmaster` | Поиск мероприятий, площадок или достопримечательностей на Ticketmaster с возможностями фильтрации по диапазону дат, ... |

## Возможности

- Поиск мероприятий: Находите предстоящие события по ключевым словам, диапазону дат, местоположению и многому другому
- Поиск площадок: Открывайте для себя площадки по названию, местоположению или специфическим критериям
- Поиск достопримечательностей: Ищите артистов, спортивные команды и другие достопримечательности
- Комплексная фильтрация: Фильтруйте результаты по дате, местоположению, площадке, достопримечательности и классификации
- HTTP транспорт: Использует потоковый HTTP транспорт для связи в реальном времени
- TypeScript реализация с комплексной обработкой ошибок

## Переменные окружения

### Обязательные
- `TICKETMASTER_API_KEY` - Необходим для работы клиента (передается на сервер)

### Опциональные
- `PORT` - Порт сервера (по умолчанию: 3000)
- `GEMINI_API_KEY` - Необходим для клиентского примера

## Примеры использования

```
Find Taylor Swift events in New York
```

```
Search for Madison Square Garden venue information
```

```
Look up Lakers sports events
```

```
Find music events in California between specific dates
```

```
Search for venues with specific capacity requirements
```

## Ресурсы

- [GitHub Repository](https://github.com/mochow13/ticketmaster-mcp-server)

## Примечания

Начиная с версии v1.1.0, API ключ TicketMaster теперь передается с клиента на сервер, поэтому никаких переменных окружения для самого сервера не требуется. Сервер по умолчанию работает на порту 3000 и включает комплексную обработку ошибок для API ошибок, валидации, сетевых проблем и аутентификации.