---
title: DeFi Rates MCP сервер
description: MCP сервер, который предоставляет AI-ассистентам доступ к данным о процентных ставках DeFi-кредитования в реальном времени по 13+ протоколам, включая Aave, Morpho, Compound, Venus и другие на множественных блокчейнах.
tags:
- Finance
- API
- Analytics
- Database
author: qingfeng
featured: false
---

MCP сервер, который предоставляет AI-ассистентам доступ к данным о процентных ставках DeFi-кредитования в реальном времени по 13+ протоколам, включая Aave, Morpho, Compound, Venus и другие на множественных блокчейнах.

## Установка

### Глобальная установка через NPM

```bash
npm install -g @asahi001/defi-rates-mcp
```

### Из исходного кода

```bash
git clone https://github.com/qingfeng/defi-rates-mcp.git
cd defi-rates-mcp
npm install
```

## Конфигурация

### Claude Desktop (NPM)

```json
{
  "mcpServers": {
    "defi-rates": {
      "command": "npx",
      "args": ["-y", "@asahi001/defi-rates-mcp"]
    }
  }
}
```

### Claude Desktop (исходный код)

```json
{
  "mcpServers": {
    "defi-rates": {
      "command": "node",
      "args": ["/path/to/defi-rates-mcp/index.js"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_latest_rates` | Получить последние процентные ставки кредитования с опциональными фильтрами по платформе, сети, активу, залогу и лимиту |
| `get_dbi_index` | Получить DBI (DeFi Borrow Index) - взвешенное среднее ставок заимствования стейблкоинов по основным прот... |
| `search_best_rates` | Найти лучшие ставки заимствования или предоставления для конкретного актива по платформам |
| `calculate_looping_strategy` | Рассчитать метрики стратегии с использованием кредитного плеча для заданной платформы, актива, залога и коэффициента LTV |
| `compare_platforms` | Сравнить ставки по разным платформам для одной и той же пары активов |

## Возможности

- Поддерживается 13+ протоколов: Aave, Morpho, Compound, Venus, Lista, Moonwell, Euler, Drift, Solend, Jupiter и другие
- Данные в реальном времени обновляются каждый час из продакшн DeFi-протоколов
- Поддержка множественных сетей: Ethereum, Arbitrum, Base, BSC, Solana, HyperEVM
- 5 мощных инструментов для запросов и анализа данных DeFi-кредитования
- Готовая интеграция с AI для Claude Desktop, Cline и других MCP-клиентов

## Примеры использования

```
Какие текущие ставки заимствования USDC на Aave?
```

```
Покажи мне все ставки кредитования Ethereum для залога WETH
```

```
Найди лучшие ставки предоставления USDT по всем платформам
```

```
Где самое дешевое место для заимствования USDC?
```

```
Рассчитай стратегию с использованием плеча на Aave, используя 10 ETH в качестве залога (цена ETH $3000) при 75% LTV для заимствования USDC
```

## Ресурсы

- [GitHub Repository](https://github.com/qingfeng/defi-rates-mcp)

## Примечания

Источник данных: https://defiborrow.loan с API-эндпоинтом, обновляемым каждый час. Требует Node.js 18+ и поддерживает протокол stdio transport для других MCP-клиентов.