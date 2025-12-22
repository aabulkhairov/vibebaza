---
title: Metricool MCP сервер
description: MCP сервер для работы с Metricool API, позволяющий получать метрики социальных сетей, данные кампаний и планировать публикации на множестве социальных платформ.
tags:
- Analytics
- API
- Media
- Integration
- Productivity
author: Community
featured: false
---

MCP сервер для работы с Metricool API, позволяющий получать метрики социальных сетей, данные кампаний и планировать публикации на множестве социальных платформ.

## Установка

### uvx

```bash
uvx --upgrade mcp-metricool
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "mcp-metricool": {
            "command": "uvx",
            "args": [
                "--upgrade",
                "mcp-metricool"
            ],
            "env": {
                "METRICOOL_USER_TOKEN": "<METRICOOL_USER_TOKEN>",
                "METRICOOL_USER_ID": "<METRICOOL_USER_ID>"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_brands` | Получить список брендов из вашего аккаунта Metricool. Упрощенный инструмент для вспомогательного использования в других инструментах... |
| `get_brands_complete` | Получить список брендов из вашего аккаунта Metricool со всей доступной информацией для каждого бренда... |
| `get_instagram_reels` | Получить список Instagram Reels из вашего аккаунта Metricool. |
| `get_instagram_posts` | Получить список постов Instagram из вашего аккаунта Metricool. |
| `get_instagram_stories` | Получить список историй Instagram из вашего аккаунта Metricool. |
| `get_tiktok_videos` | Получить список видео TikTok из вашего аккаунта Metricool. |
| `get_facebook_reels` | Получить список Facebook Reels из вашего аккаунта Metricool. |
| `get_facebook_posts` | Получить список постов Facebook из вашего аккаунта бренда Metricool. |
| `get_facebook_stories` | Получить список историй Facebook из вашего аккаунта бренда Metricool. |
| `get_thread_posts` | Получить список постов Threads из вашего аккаунта бренда Metricool. |
| `get_x_posts` | Получить список постов X (Twitter) из вашего аккаунта Metricool. |
| `get_bluesky_posts` | Получить список постов Bluesky из вашего аккаунта бренда Metricool. |
| `get_linkedin_posts` | Получить список постов LinkedIn из вашего аккаунта бренда Metricool. |
| `get_pinterest_pins` | Получить список пинов Pinterest из вашего аккаунта бренда Metricool. |
| `get_youtube_videos` | Получить список видео YouTube из вашего аккаунта бренда Metricool. |

## Возможности

- Доступ и анализ метрик социальных сетей на множестве платформ
- Получение данных кампаний из Facebook Ads, Google Ads и TikTok Ads
- Планирование постов и мультипостов для ваших брендов
- Анализ постов конкурентов и их производительности
- Получение оптимального времени для публикаций в разных социальных сетях
- Доступ к контенту из Instagram, Facebook, TikTok, Twitter/X, LinkedIn, YouTube, Pinterest, Twitch, Threads и Bluesky
- Управление запланированными постами и контентными календарями

## Переменные окружения

### Обязательные
- `METRICOOL_USER_TOKEN` - Ваш токен API Metricool
- `METRICOOL_USER_ID` - Ваш ID пользователя Metricool

## Ресурсы

- [GitHub Repository](https://github.com/metricool/mcp-metricool)

## Примечания

Требуется аккаунт Metricool с доступом к API (тариф Advanced). Необходим Python 3.8 или выше вместе с uv и git. Расположение файлов конфигурации зависит от ОС: macOS использует ~/Library/Application Support/Claude/claude_desktop_config.json, Windows использует %APPDATA%/Claude/claude_desktop_config.json.