---
title: Virtual location (Google Street View,etc.) MCP сервер
description: MCP сервер, который создает виртуальную среду для путешествий, используя Google Maps и Street View. Позволяет аватарам путешествовать виртуально с генерацией изображений и интеграцией с социальными сетями для отчетов о прогрессе путешествий.
tags:
- AI
- API
- Media
- Integration
- Web Scraping
author: Community
featured: false
---

MCP сервер, который создает виртуальную среду для путешествий, используя Google Maps и Street View. Позволяет аватарам путешествовать виртуально с генерацией изображений и интеграцией с социальными сетями для отчетов о прогрессе путешествий.

## Установка

### NPX

```bash
npx -y @mfukushim/map-traveler-mcp
```

### NPX (v0.0.81 stdio)

```bash
npx -y @mfukushim/map-traveler-mcp@0.0.81
```

## Конфигурация

### Claude Desktop (stdio type)

```json
{
  "mcpServers": {
    "traveler": {
      "command": "npx",
      "args": ["-y", "@mfukushim/map-traveler-mcp"],
      "env":{
        "MT_GOOGLE_MAP_KEY":"(Google Map API key)",
        "MT_GEMINI_IMAGE_KEY": "(Gemini Image Api key)",
        "MT_SQLITE_PATH":"(db save path)"
      }
    }
  }
}
```

### Claude Desktop (streamable-http type)

```json
{
  "mcpServers": {
    "traveler": {
      "type": "streamable-http",
      "url": "https://(mcp server address)/mcp?config=(base64 config json)"
    }
  }
}
```

### Режим практики

```json
{
  "mcpServers": {
    "traveler": {
      "command": "npx",
      "args": ["-y", "@mfukushim/map-traveler-mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_traveler_view_info` | Получает информацию о текущем местоположении аватара путешественника с опциональными фото и близлежащими объектами... |
| `get_traveler_location` | Получает информацию о текущем адресе аватара путешественника и близлежащих объектах |
| `reach_a_percentage_of_destination` | Достигнуть указанного процента от пункта назначения (только moveMode=skip) |
| `set_traveler_location` | Устанавливает текущее местоположение аватара путешественника |
| `get_traveler_destination_address` | Получить пункт назначения аватара путешественника, который вы установили |
| `set_traveler_destination_address` | Установить пункт назначения аватара путешественника |
| `start_traveler_journey` | Начать путешествие к пункту назначения (только moveMode=realtime) |
| `stop_traveler_journey` | Остановить путешествие (только moveMode=realtime) |
| `set_traveler_info` | Установить атрибуты путешественника, такие как имя и личность |
| `get_traveler_info` | Получить атрибуты и личность путешественника |
| `set_avatar_prompt` | Установить промпт для генерации изображения аватара путешественника |
| `reset_avatar_prompt` | Сбросить промпты генерации аватара к значениям по умолчанию |
| `get_sns_feeds` | Получает статьи Bluesky SNS для указанной пользовательской ленты |
| `get_sns_mentions` | Получает недавние упоминания (лайки, ответы) к постам Bluesky SNS |
| `post_sns_writer` | Публикует статью в Bluesky SNS с указанной пользовательской лентой |

## Возможности

- Виртуальные путешествия по Google Maps с симуляцией аватара
- Интеграция с фотографиями Google Street View с композицией аватара
- Поддержка множественных API для генерации изображений (Gemini, PixAI, Stability.ai, ComfyUI)
- Интеграция с Bluesky SNS для отчетов о путешествиях и социального взаимодействия
- Поддержка протоколов MCP как stdio, так и streamable-HTTP
- Режимы путешествий в реальном времени и с пропусками
- Многопользовательская поддержка с управлением сессиями
- Пользовательские ресурсы промптов для различных сценариев путешествий
- Поддержка nano-banana семантических масок для ускоренной генерации изображений
- Поиск близлежащих объектов и информации о местоположении

## Переменные окружения

### Обязательные
- `MT_GOOGLE_MAP_KEY` - Google Map API ключ

### Опциональные
- `MT_GEMINI_IMAGE_KEY` - Gemini Image Api ключ
- `MT_MAX_RETRY_GEMINI` - Количество повторных попыток при генерации изображений Gemini (По умолчанию: 0)
- `MT_AVATAR_IMAGE_URI` - URI эталонного изображения персонажа при генерации изображений Gemini
- `MT_SQLITE_PATH` - Путь сохранения базы данных
- `MT_TURSO_URL` - Turso sqlite API URL
- `MT_TURSO_TOKEN` - Turso sqlite API токен доступа
- `MT_PIXAI_KEY` - PixAI API ключ
- `MT_SD_KEY` - Stability.ai API ключ для генерации изображений

## Примеры использования

```
Где ты сейчас?
```

```
Давай отправимся на станцию Токио.
```

```
Отправляйся в путешествие.
```

```
Начни путешествие к месту назначения.
```

```
Покажи мне фотографии текущего местоположения.
```

## Ресурсы

- [GitHub Repository](https://github.com/mfukushim/map-traveler-mcp)

## Примечания

Требует Google Maps API с разрешениями Street View Static API, Places API (New), Time Zone API и Directions API. Поддерживает режим практики без API ключей. Включает пользовательские ресурсы промптов для ролевых сценариев. Совместим с платформами LibreChat, Smithery.ai и MseeP.