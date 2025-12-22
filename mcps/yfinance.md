---
title: yfinance MCP сервер
description: Сервер котировок акций на базе Yahoo Finance API, который позволяет AI агентам получать данные акций в реальном времени, управлять списками отслеживания, проводить технический анализ и рассчитывать финансовые индикаторы через MCP интеграцию.
tags:
- Finance
- API
- Analytics
- AI
- Integration
author: Adity-star
featured: false
---

Сервер котировок акций на базе Yahoo Finance API, который позволяет AI агентам получать данные акций в реальном времени, управлять списками отслеживания, проводить технический анализ и рассчитывать финансовые индикаторы через MCP интеграцию.

## Установка

### Из исходного кода с uv

```bash
# Install uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# Create and navigate to project directory
mkdir mcp-yfinance-server
cd mcp-yfinance-server

# Initialize project
uv init

# Create and activate virtual environment
uv venv
source .venv/bin/activate

# Install the project
uv pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "yfinance-price-tracker": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/YOUR/mcp-yfinance-server",
        "run",
        "main.py"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `add_to_watchlist` | Добавить тикер акции в ваш персональный список отслеживания |
| `analyze_stock` | Провести месячный технический анализ трендов (RSI, MACD, MA) |
| `get_technical_summary` | Создать комплексную техническую сводку с индикаторами и сигналами |
| `get_watchlist_prices` | Получить актуальные цены для всех тикеров из списка отслеживания |
| `get_trend_analysis` | Проанализировать недавние смены трендов, паттерны и дивергенции |
| `get_stock_price` | Получить текущую цену для указанного символа тикера |
| `get_volatility_analysis` | Рассчитать историческую волатильность и метрики ATR |
| `compare_stocks` | Сравнить цены двух акций (полезно для анализа относительной доходности) |

## Возможности

- Получение данных акций в реальном времени
- Управление списком отслеживания
- Проведение полного анализа акций
- Расчет полного набора технических индикаторов
- Динамическое управление списками отслеживания
- Определение трендов и моментума
- Углубленный технический анализ для инвестиционных решений
- Оценка рисков на основе волатильности
- 18+ мощных инструментов для анализа акций
- Создание визуальных графиков и инсайтов

## Примеры использования

```
Compare the stock prices of Tesla and Apple
```

```
Get the historical data for Tesla over the past month
```

```
Add Apple, Tesla, and Reliance to my watchlist
```

```
Show me a chart of Apple's stock over the last 30 days
```

## Ресурсы

- [GitHub Repository](https://github.com/Adity-star/mcp-yfinance-server)

## Примечания

Сервер предоставляет 18 инструментов для комплексного анализа акций. Включает поддержку MCP Server Inspector для тестирования инструментов. Требует перезапуска Claude Desktop после конфигурации. Связан с более простым проектом трекера криптовалют для начинающих.