---
title: Travel Planner MCP сервер
description: Travel Planner MCP сервер, который интегрируется с Google Maps API, позволяя LLM выполнять задачи, связанные с путешествиями — поиск локаций, получение детальной информации о местах, расчет маршрутов и получение информации о часовых поясах.
tags:
- API
- Search
- Integration
- Productivity
author: GongRzhe
featured: false
install_command: npx -y @smithery/cli install @GongRzhe/TRAVEL-PLANNER-MCP-Server
  --client claude
---

Travel Planner MCP сервер, который интегрируется с Google Maps API, позволяя LLM выполнять задачи, связанные с путешествиями — поиск локаций, получение детальной информации о местах, расчет маршрутов и получение информации о часовых поясах.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @GongRzhe/TRAVEL-PLANNER-MCP-Server --client claude
```

### NPX (Рекомендуется)

```bash
npx @gongrzhe/server-travelplanner-mcp
```

### NPX с API ключом

```bash
GOOGLE_MAPS_API_KEY=your_api_key npx @gongrzhe/server-travelplanner-mcp
```

### Глобальная установка

```bash
npm install -g @gongrzhe/server-travelplanner-mcp
GOOGLE_MAPS_API_KEY=your_api_key @gongrzhe/server-travelplanner-mcp
```

### Из исходного кода

```bash
git clone repository
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "travel-planner": {
      "command": "npx",
      "args": ["@gongrzhe/server-travelplanner-mcp"],
      "env": {
        "GOOGLE_MAPS_API_KEY": "your_google_maps_api_key"
      }
    }
  }
}
```

### Claude Desktop (Node)

```json
{
  "mcpServers": {
    "travel-planner": {
      "command": "node",
      "args": ["path/to/dist/index.js"],
      "env": {
        "GOOGLE_MAPS_API_KEY": "your_google_maps_api_key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `searchPlaces` | Поиск мест с помощью Google Places API с возможностью привязки к локации и настройкой радиуса |
| `getPlaceDetails` | Получение детальной информации о конкретном месте с использованием Google Place ID |
| `calculateRoute` | Расчет маршрута между двумя точками с различными режимами передвижения (автомобиль, пешком, велосипед, общественный транспорт...) |
| `getTimeZone` | Получение информации о часовом поясе для локации с использованием координат и опционального временного штампа |

## Возможности

- Поиск локаций с помощью Google Places API
- Получение детальной информации о местах через Google Place IDs
- Расчет маршрутов между локациями
- Поддержка различных режимов передвижения (автомобиль, пешком, велосипед, общественный транспорт)
- Получение информации о часовых поясах
- Результаты поиска с привязкой к локации
- Настраиваемый радиус поиска

## Переменные окружения

### Обязательные
- `GOOGLE_MAPS_API_KEY` - Google Maps API ключ с включенными Places API, Directions API, Geocoding API и Time Zone API

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/TRAVEL-PLANNER-MCP-Server)

## Примечания

Требует Google Maps API ключ с включенными несколькими API (Places, Directions, Geocoding, Time Zone). Лицензия MIT License.