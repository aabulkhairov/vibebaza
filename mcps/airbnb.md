---
title: Airbnb MCP сервер
description: Расширение для поиска объявлений Airbnb с продвинутыми фильтрами и получением
  детальной информации о недвижимости, реализованное как MCP сервер.
tags:
- Search
- Web Scraping
- API
- Productivity
- Integration
author: openbnb-org
featured: true
---

Расширение для поиска объявлений Airbnb с продвинутыми фильтрами и получением детальной информации о недвижимости, реализованное как MCP сервер.

## Установка

### NPX

```bash
npx -y @openbnb/mcp-server-airbnb
```

### NPX (игнорировать robots.txt)

```bash
npx -y @openbnb/mcp-server-airbnb --ignore-robots-txt
```

### Из исходников

```bash
npm install
npm run build
node dist/index.js
```

### DXT файл

```bash
Download the .dxt file from releases page and install through compatible AI application's extension manager
```

## Конфигурация

### Cursor базовая

```json
{
  "mcpServers": {
    "airbnb": {
      "command": "npx",
      "args": [
        "-y",
        "@openbnb/mcp-server-airbnb"
      ]
    }
  }
}
```

### Cursor (игнорировать robots.txt)

```json
{
  "mcpServers": {
    "airbnb": {
      "command": "npx",
      "args": [
        "-y",
        "@openbnb/mcp-server-airbnb",
        "--ignore-robots-txt"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `airbnb_search` | Поиск объявлений Airbnb с фильтрами: локация, даты, гости и др. |
| `airbnb_listing_details` | Детальная информация об объявлении: удобства, правила, характеристики |

## Возможности

- Поиск по локации: города, штаты, регионы
- Интеграция с Google Maps Place ID для точного таргетинга локации
- Фильтрация по датам с поддержкой check-in и check-out
- Настройка гостей: взрослые, дети, младенцы, питомцы
- Фильтрация по цене с минимумом и максимумом
- Пагинация для просмотра больших наборов результатов
- Детали объявлений: удобства, правила, highlights
- Информация о локации с координатами и деталями района
- Правила дома и политики для информированного бронирования
- Прямые ссылки на объявления Airbnb для простого бронирования

## Примеры использования

```
Search for Airbnb listings in San Francisco for 2 adults
```

```
Find properties in a specific location with check-in and check-out dates
```

```
Get detailed information about a specific Airbnb listing
```

```
Search for accommodations with price filtering and guest requirements
```

```
Browse through paginated search results for large result sets
```

## Ресурсы

- [GitHub Repository](https://github.com/openbnb-org/mcp-server-airbnb)

## Примечания

Расширение по умолчанию соблюдает robots.txt и включает меры безопасности: лимиты таймаута запросов и валидация ввода. Не аффилировано с Airbnb, Inc. и предназначено для легитимных исследований и помощи в бронировании. Требуется Node.js 18+ и совместимость с Claude Desktop 0.10.0 или выше.
