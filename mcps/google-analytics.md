---
title: Google Analytics MCP сервер
description: MCP сервер, который подключает данные Google Analytics 4 к Claude, Cursor и другим MCP клиентам, позволяя делать запросы на естественном языке по более чем 200 измерениям и метрикам GA4 для анализа трафика сайта и поведения пользователей.
tags:
- Analytics
- API
- Integration
- Productivity
- Monitoring
author: surendranb
featured: true
---

MCP сервер, который подключает данные Google Analytics 4 к Claude, Cursor и другим MCP клиентам, позволяя делать запросы на естественном языке по более чем 200 измерениям и метрикам GA4 для анализа трафика сайта и поведения пользователей.

## Установка

### pip install

```bash
pip install google-analytics-mcp
```

### Из исходников

```bash
git clone https://github.com/surendranb/google-analytics-mcp.git
cd google-analytics-mcp
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop (python3)

```json
{
  "mcpServers": {
    "ga4-analytics": {
      "command": "python3",
      "args": ["-m", "ga4_mcp_server"],
      "env": {
        "GOOGLE_APPLICATION_CREDENTIALS": "/path/to/your/service-account-key.json",
        "GA4_PROPERTY_ID": "123456789"
      }
    }
  }
}
```

### Claude Desktop (python)

```json
{
  "mcpServers": {
    "ga4-analytics": {
      "command": "python",
      "args": ["-m", "ga4_mcp_server"],
      "env": {
        "GOOGLE_APPLICATION_CREDENTIALS": "/path/to/your/service-account-key.json",
        "GA4_PROPERTY_ID": "123456789"
      }
    }
  }
}
```

### Из исходников

```json
{
  "mcpServers": {
    "ga4-analytics": {
      "command": "/full/path/to/ga4-mcp-server/venv/bin/python",
      "args": ["/full/path/to/ga4-mcp-server/ga4_mcp_server.py"],
      "env": {
        "GOOGLE_APPLICATION_CREDENTIALS": "/path/to/your/service-account-key.json",
        "GA4_PROPERTY_ID": "123456789"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_schema` | Поиск ключевого слова по всем доступным измерениям и метрикам |
| `get_ga4_data` | Получение данных GA4 со встроенным интеллектом, включая защиту объема данных, умную агрегацию,... |
| `list_dimension_categories` | Список всех доступных категорий измерений |
| `list_metric_categories` | Список всех доступных категорий метрик |
| `get_dimensions_by_category` | Получение всех измерений для определенной категории |
| `get_metrics_by_category` | Получение всех метрик для определенной категории |
| `get_property_schema` | Возвращает полную схему для свойства |

## Возможности

- Доступ к более чем 200 измерениям и метрикам GA4
- Умное управление объемом данных с автоматической оценкой строк
- Встроенные оптимизации для предотвращения сбоев контекстного окна
- Серверная обработка с интеллектуальной агрегацией
- Интерактивные предупреждения для больших наборов данных с предложениями по оптимизации
- Возможности многомерного анализа
- Географический анализ, анализ источников трафика и электронной коммерции
- Фильтрация по времени и сравнения период к периоду
- Анализ производительности контента и поведения пользователей

## Переменные окружения

### Обязательные
- `GOOGLE_APPLICATION_CREDENTIALS` - Путь к JSON файлу ключа сервисного аккаунта Google
- `GA4_PROPERTY_ID` - ID свойства Google Analytics 4 (числовой)

## Примеры использования

```
Какие категории измерений GA4 доступны?
```

```
Покажи мне все метрики электронной коммерции
```

```
Какой трафик на моем сайте за прошлую неделю?
```

```
Покажи метрики пользователей по городам за прошлый месяц
```

```
Покажи доходы по странам и категориям устройств за последние 30 дней
```

## Ресурсы

- [GitHub Repository](https://github.com/surendranb/google-analytics-mcp)

## Примечания

Требует свойство Google Analytics 4 с данными и сервисный аккаунт с доступом к Analytics Reporting API. Включает встроенные оптимизации производительности, такие как автоматическая оценка строк, интерактивные предупреждения для больших наборов данных и умное управление объемом данных для предотвращения сбоев контекстного окна.