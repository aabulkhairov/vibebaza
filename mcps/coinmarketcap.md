---
title: CoinMarketCap MCP сервер
description: Реализация Model Context Protocol сервера для CoinMarketCap API, предоставляющая стандартизированный доступ к данным криптовалютного рынка, информации об обменниках и блокчейн-метрикам с полным покрытием API.
tags:
- API
- Finance
- Analytics
- Database
author: Community
featured: false
---

Реализация Model Context Protocol сервера для CoinMarketCap API, предоставляющая стандартизированный доступ к данным криптовалютного рынка, информации об обменниках и блокчейн-метрикам с полным покрытием API.

## Установка

### Smithery Remote Server

```bash
npx -y @smithery/cli install @shinzo-labs/coinmarketcap-mcp
```

### NPX

```bash
npx @shinzolabs/coinmarketcap-mcp
```

### Из исходного кода

```bash
git clone https://github.com/shinzo-labs/coinmarketcap-mcp.git
pnpm i
```

## Конфигурация

### Конфигурация NPX

```json
{
  "mcpServers": {
    "coinmarketcap": {
      "command": "npx",
      "args": [
        "@shinzolabs/coinmarketcap-mcp"
      ],
      "env": {
        "COINMARKETCAP_API_KEY": "your-key-here",
        "SUBSCRIPTION_LEVEL": "Basic"
      }
    }
  }
}
```

### Конфигурация из исходного кода

```json
{
  "mcpServers": {
    "coinmarketcap": {
      "command": "node",
      "args": [
        "/path/to/coinmarketcap-mcp/index.js"
      ],
      "env": {
        "COINMARKETCAP_API_KEY": "your-key-here",
        "SUBSCRIPTION_LEVEL": "Basic"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `cryptoCurrencyMap` | Получить маппинг всех криптовалют |
| `getCryptoMetadata` | Получить метаданные для одной или нескольких криптовалют |
| `allCryptocurrencyListings` | Получить последние рыночные котировки для 1-5000 криптовалют |
| `cryptoQuotesLatest` | Получить последние рыночные котировки для одной или нескольких криптовалют |
| `cryptoCategories` | Получить список всех категорий криптовалют |
| `cryptoCategory` | Получить метаданные о категории криптовалют |
| `exchangeMap` | Получить маппинг всех обменников |
| `exchangeInfo` | Получить метаданные для одного или нескольких обменников |
| `exchangeAssets` | Получить список всех активов, доступных на обменнике |
| `dexInfo` | Получить метаданные для одной или нескольких децентрализованных бирж |
| `dexListingsLatest` | Получить последние рыночные данные для всех DEX |
| `globalMetricsLatest` | Получить последние глобальные метрики криптовалют |
| `cmc100IndexLatest` | Получить последнее значение индекса CoinMarketCap 100 и его составляющие |
| `priceConversion` | Конвертировать сумму одной криптовалюты или фиатной валюты в другую |
| `fearAndGreedLatest` | Получить последний индекс страха и жадности |

## Возможности

- Полное покрытие CoinMarketCap API
- Получение данных о последних крипто-трендах, рыночных движениях и глобальных рыночных метриках
- Доступ к детальным OHLCV данным с подпиской Standard или выше
- Типобезопасная валидация параметров с Zod

## Переменные окружения

### Обязательные
- `COINMARKETCAP_API_KEY` - API ключ с CoinMarketCap.com

### Опциональные
- `SUBSCRIPTION_LEVEL` - Basic, Hobbyist, Startup, Standard, Professional, или Enterprise
- `PORT` - Порт для Streamable HTTP транспортного метода
- `TELEMETRY_ENABLED` - Включить телеметрию

## Ресурсы

- [GitHub Repository](https://github.com/shinzo-labs/coinmarketcap-mcp)

## Примечания

Требуется API ключ CoinMarketCap (доступен бесплатный Basic ключ). Различные инструменты доступны в зависимости от уровня подписки (Basic, Hobbyist, Startup, Standard, Professional, Enterprise). Анонимная телеметрия собирается по умолчанию, но может быть отключена.