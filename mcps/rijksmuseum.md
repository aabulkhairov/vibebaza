---
title: Rijksmuseum MCP сервер
description: Model Context Protocol (MCP) сервер, который предоставляет доступ к коллекции Rijksmuseum через естественное языковое взаимодействие, позволяя AI моделям исследовать, анализировать и взаимодействовать с произведениями искусства и коллекциями.
tags:
- API
- Search
- Media
- Analytics
- Integration
author: r-huijts
featured: false
---

Model Context Protocol (MCP) сервер, который предоставляет доступ к коллекции Rijksmuseum через естественное языковое взаимодействие, позволяя AI моделям исследовать, анализировать и взаимодействовать с произведениями искусства и коллекциями.

## Установка

### NPX

```bash
npx -y mcp-server-rijksmuseum
```

### Из исходного кода

```bash
git clone [repository]
npm install
cp .env.example .env
# Add your API key to .env file
```

## Конфигурация

### Claude Desktop (NPM)

```json
{
  "mcpServers": {
    "rijksmuseum-server": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-server-rijksmuseum"
      ],
      "env": {
        "RIJKSMUSEUM_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Claude Desktop (из исходного кода)

```json
{
  "mcpServers": {
    "rijksmuseum-server": {
      "command": "node",
      "args": [
        "/path/to/rijksmuseum-server/build/index.js"
      ],
      "env": {
        "RIJKSMUSEUM_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_artwork` | Поиск и фильтрация произведений искусства по различным критериям, включая текстовый поиск, имя художника, произведения... |
| `get_artwork_details` | Получение подробной информации о конкретных произведениях искусства, включая базовые данные, физические свойства... |
| `get_artwork_image` | Доступ к данным изображений высокого разрешения с возможностями глубокого масштабирования, множественными уровнями зума, тайловой системой... |
| `get_user_sets` | Просмотр пользовательских коллекций и курируемых наборов |
| `get_user_set_details` | Доступ к подробной информации о конкретных пользовательских коллекциях, включая тематические группировки... |
| `open_image_in_browser` | Открытие изображений произведений искусства напрямую в браузере для детального просмотра |
| `get_artist_timeline` | Генерация хронологических временных линий работ художников для отслеживания художественного развития, анализа периодов... |

## Возможности

- Поиск и фильтрация произведений искусства по различным критериям
- Получение исчерпывающей информации и метаданных о произведениях искусства
- Доступ к изображениям высокого разрешения с возможностями глубокого зума
- Исследование пользовательских коллекций и курируемых наборов
- Генерация временных линий художников и анализ карьерного развития
- Открытие изображений произведений искусства напрямую в браузере
- Поддержка текстового поиска по всей коллекции
- Фильтрация по художнику, типу произведения, материалам, техникам, временным периодам и цветам

## Переменные окружения

### Обязательные
- `RIJKSMUSEUM_API_KEY` - Ваш API ключ Rijksmuseum

### Опциональные
- `PORT` - Порт сервера
- `LOG_LEVEL` - Уровень логирования

## Примеры использования

```
Show me all paintings by Rembrandt from the 1640s
```

```
Find artworks that prominently feature the color blue
```

```
What are the most famous masterpieces in the collection?
```

```
Tell me everything about The Night Watch
```

```
Show me high-resolution details of the brushwork in Vermeer's The Milkmaid
```

## Ресурсы

- [GitHub Repository](https://github.com/r-huijts/rijksmuseum-mcp)

## Примечания

Требует API ключ Rijksmuseum, который можно получить через Rijksmuseum API Portal (https://data.rijksmuseum.nl/docs/api/). Сервер предоставляет доступ к обширной коллекции Rijksmuseum с подробной информацией о произведениях искусства, изображениями высокого разрешения и пользовательскими коллекциями.