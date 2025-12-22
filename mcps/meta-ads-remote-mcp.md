---
title: Meta Ads Remote MCP сервер
description: Model Context Protocol сервер для взаимодействия с Meta Ads — анализируйте, управляйте и оптимизируйте рекламные кампании в Facebook, Instagram и других платформах Meta через AI интерфейс.
tags:
- API
- Analytics
- AI
- Integration
- CRM
author: Community
featured: false
---

Model Context Protocol сервер для взаимодействия с Meta Ads — анализируйте, управляйте и оптимизируйте рекламные кампании в Facebook, Instagram и других платформах Meta через AI интерфейс.

## Установка

### Remote MCP (Рекомендуется)

```bash
Use cloud service at https://mcp.pipeboard.co/meta-ads-mcp
```

### Локальная установка

```bash
See STREAMABLE_HTTP_SETUP.md for complete instructions
```

## Конфигурация

### Claude Desktop

```json
Name: "Pipeboard Meta Ads"
Integration URL: https://mcp.pipeboard.co/meta-ads-mcp
```

### Cursor

```json
{
  "mcpServers": {
    "meta-ads-remote": {
      "url": "https://mcp.pipeboard.co/meta-ads-mcp"
    }
  }
}
```

### Cursor с токеном

```json
{
  "mcpServers": {
    "meta-ads-remote": {
      "url": "https://mcp.pipeboard.co/meta-ads-mcp?token=YOUR_PIPEBOARD_TOKEN"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `mcp_meta_ads_get_ad_accounts` | Получить рекламные аккаунты, доступные пользователю |
| `mcp_meta_ads_get_account_info` | Получить детальную информацию о конкретном рекламном аккаунте |
| `mcp_meta_ads_get_account_pages` | Получить страницы, связанные с аккаунтом Meta Ads |
| `mcp_meta_ads_get_campaigns` | Получить кампании для аккаунта Meta Ads с возможностью фильтрации |
| `mcp_meta_ads_get_campaign_details` | Получить детальную информацию о конкретной кампании |
| `mcp_meta_ads_create_campaign` | Создать новую кампанию в аккаунте Meta Ads |
| `mcp_meta_ads_get_adsets` | Получить наборы объявлений для аккаунта Meta Ads с возможностью фильтрации по кампаниям |
| `mcp_meta_ads_get_adset_details` | Получить детальную информацию о конкретном наборе объявлений |
| `mcp_meta_ads_create_adset` | Создать новый набор объявлений в аккаунте Meta Ads |
| `mcp_meta_ads_get_ads` | Получить объявления для аккаунта Meta Ads с возможностью фильтрации |
| `mcp_meta_ads_create_ad` | Создать новое объявление с существующим креативом |
| `mcp_meta_ads_get_ad_details` | Получить детальную информацию о конкретном объявлении |
| `mcp_meta_ads_get_ad_creatives` | Получить детали креативов для конкретного объявления |
| `mcp_meta_ads_create_ad_creative` | Создать новый рекламный креатив, используя хеш загруженного изображения |
| `mcp_meta_ads_update_ad_creative` | Обновить существующий рекламный креатив с новым контентом или настройками |

## Возможности

- AI-анализ кампаний
- Стратегические рекомендации
- Автоматический мониторинг
- Оптимизация бюджета
- Улучшение креативов
- Динамическое тестирование креативов
- Управление кампаниями
- Кросс-платформенная интеграция (Facebook, Instagram, все платформы Meta)
- Поддержка универсальных LLM
- Расширенный поиск с поиском по страницам

## Примеры использования

```
Analyze your campaigns and provide actionable insights on performance
```

```
Track performance metrics and alert about significant changes
```

```
Get recommendations for reallocating budget to better-performing ad sets
```

```
Receive feedback on ad copy, imagery, and calls-to-action
```

```
Request changes to campaigns, ad sets, and ads
```

## Ресурсы

- [GitHub Repository](https://github.com/pipeboard-co/meta-ads-mcp)

## Примечания

Это неофициальный сторонний инструмент, не связанный с Meta. Remote MCP настоятельно рекомендуется вместо локальной установки для более быстрой и надежной настройки. Прямая аутентификация по токену доступна с помощью параметра ?token=YOUR_PIPEBOARD_TOKEN. Получить токены можно на pipeboard.co/api-tokens.