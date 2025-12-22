---
title: TikTok Ads MCP сервер
description: Model Context Protocol сервер для интеграции с TikTok Ads API, который позволяет AI-ассистентам взаимодействовать с рекламными кампаниями TikTok, предоставляя комплексные возможности управления кампаниями, аналитики и оптимизации.
tags:
- API
- Analytics
- Productivity
- Integration
- Media
author: AdsMCP
featured: false
---

Model Context Protocol сервер для интеграции с TikTok Ads API, который позволяет AI-ассистентам взаимодействовать с рекламными кампаниями TikTok, предоставляя комплексные возможности управления кампаниями, аналитики и оптимизации.

## Установка

### Из исходного кода

```bash
# Clone the repository
git clone <repository-url>
cd adsmcp-server

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -e .
```

### Используя uv (рекомендуется)

```bash
# Install with uv
uv sync
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "tiktok-ads": {
      "command": "python",
      "args": ["/path/to/adsmcp-server/run_server.py"],
      "cwd": "/path/to/adsmcp-server",
      "env": {
        "TIKTOK_APP_ID": "your_app_id",
        "TIKTOK_APP_SECRET": "your_app_secret"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `tiktok_ads_login` | Запуск процесса OAuth-аутентификации TikTok Ads |
| `tiktok_ads_complete_auth` | Завершение OAuth-аутентификации с кодом авторизации |
| `tiktok_ads_auth_status` | Проверка текущего статуса аутентификации |
| `tiktok_ads_switch_ad_account` | Переключение на другой рекламный аккаунт |
| `tiktok_ads_get_campaigns` | Получение всех кампаний для рекламного аккаунта |
| `tiktok_ads_get_campaign_details` | Получение подробной информации о конкретной кампании |
| `tiktok_ads_get_adgroups` | Получение рекламных групп для кампании |
| `tiktok_ads_get_campaign_performance` | Получение метрик производительности для кампаний с поддержкой детальных метрик |
| `tiktok_ads_get_adgroup_performance` | Получение метрик производительности для рекламных групп с разбивкой |

## Возможности

- Управление кампаниями: Создание, чтение и обновление кампаний и рекламных групп
- Аналитика производительности: Получение детальных метрик производительности и инсайтов
- Управление аудиторией: Работа с пользовательскими аудиториями и параметрами таргетинга
- Управление креативами: Загрузка и управление рекламными креативами
- Отчетность: Генерация и загрузка пользовательских отчетов о производительности

## Переменные окружения

### Обязательные
- `TIKTOK_APP_ID` - Ваш ID приложения TikTok Ads API
- `TIKTOK_APP_SECRET` - Ваш секрет приложения TikTok Ads API

## Ресурсы

- [GitHub Repository](https://github.com/AdsMCP/tiktok-ads-mcp-server)

## Примечания

Этот проект является частью платформы автоматизации рекламы AdsMCP AI. Опция удаленного MCP сервера доступна на AdsMCP.com для быстрой настройки без ручной конфигурации. Требуется аккаунт TikTok For Business с доступом к API и аккаунт разработчика TikTok Ads. Сервер включает встроенное ограничение скорости и логику повторных попыток. Ограничения API: 1000 запросов в час на приложение, 10 одновременных запросов.