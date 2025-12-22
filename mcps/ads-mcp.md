---
title: Ads MCP сервер
description: Удалённый MCP сервер для планирования кампаний, исследований и кроссплатформенного
  создания рекламы. Поддерживает Google Ads Search & Performance Max и TikTok кампании
  с OAuth 2.1 аутентификацией.
tags:
- API
- Analytics
- Media
- Integration
- Productivity
author: amekala
featured: false
---

Удалённый MCP сервер для планирования кампаний, исследований и кроссплатформенного создания рекламы. Поддерживает Google Ads Search & Performance Max и TikTok кампании с OAuth 2.1 аутентификацией.

## Конфигурация

### ChatGPT

```json
Settings → Connectors → Create
Name: Ads MCP
URL: https://mcp.adspirer.com/
```

### Claude

```json
Settings → Connectors → Add custom
Name: Ads MCP
URL: https://mcp.adspirer.com/
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `help_user_upload` | Возвращает инструкции по предоставлению прямых ссылок на медиа |
| `validate_and_prepare_assets` | Скачивает и валидирует медиа по URL; возвращает asset_bundle_id с прогресс-стримом |
| `create_pmax_campaign` | Атомарное создание Performance Max кампании с паттерном validate-then-commit и прогресс-стримом |
| `create_search_campaign` | Создание текстовой Search кампании с опциональными ассетами |

## Возможности

- Планирование и валидация кампаний через структурированные промпты
- Генерация креативных вариантов и сборка compliant asset bundles
- Создание Google Ads Search и Performance Max кампаний, а также TikTok кампаний end-to-end
- Обновления прогресса в реальном времени для длительных операций (5-30 секунд)
- Progress streaming с поддержкой MCP 2025-03-26 протокола
- OAuth 2.1 аутентификация с серверными rate limits
- Tool safety аннотации с read-only и destructive hints
- Только HTTPS URL с проверками безопасности
- Retry логика скачивания изображений и совместимость с CDN

## Примеры использования

```
create a PMAX campaign for...
```

## Ресурсы

- [GitHub Repository](https://github.com/amekala/ads-mcp)

## Примечания

Это удалённый MCP сервер, доступный по адресу https://mcp.adspirer.com/ с fallback URL https://adspirer-mcp-596892545013.us-central1.run.app/. Требуется OAuth 2.1 аутентификация через Adspirer с платными тарифами и серверными rate limits. Registry ID: com.adspirer/ads. Поддержка: abhi@adspirer.com.
