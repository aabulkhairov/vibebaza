---
title: coin_api_mcp MCP сервер
description: Model Context Protocol сервер, который предоставляет доступ к криптовалютным данным CoinMarketCap, позволяя AI-приложениям получать листинги криптовалют, котировки и подробную информацию о различных монетах.
tags:
- Finance
- API
- Analytics
author: Community
featured: false
install_command: npx -y @smithery/cli install coin-api-mcp --client claude
---

Model Context Protocol сервер, который предоставляет доступ к криптовалютным данным CoinMarketCap, позволяя AI-приложениям получать листинги криптовалют, котировки и подробную информацию о различных монетах.

## Установка

### Smithery

```bash
npx -y @smithery/cli install coin-api-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/longmans/coin_api_mcp.git
cd coin_api_mcp
uv build
uv pip install .
```

### Запуск как скрипт

```bash
python -m coin_api_mcp
```

## Конфигурация

### Claude Desktop

```json
"mcpServers": {
  "coin_api": {
    "command": "python",
    "args": ["-m", "coin_api_mcp"]
  },
  "env": {
        "COINMARKETCAP_API_KEY": "your_api_key_here"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `listing-coins` | Получает постраничный список всех активных криптовалют с последними рыночными данными |
| `get-coin-info` | Извлекает подробную информацию о конкретной криптовалюте |
| `get-coin-quotes` | Получает последние рыночные котировки для одной или нескольких криптовалют |

## Возможности

- Постраничные листинги криптовалют с рыночными данными
- Возможности фильтрации по цене и рыночной капитализации
- Поддержка конвертации в несколько валют
- Получение подробной информации о криптовалютах
- Котировки в реальном времени
- Поддержка нескольких методов идентификации (ID, slug, symbol)

## Переменные окружения

### Обязательные
- `COINMARKETCAP_API_KEY` - API ключ от CoinMarketCap, необходимый для работы сервера

## Ресурсы

- [GitHub Repository](https://github.com/longmans/coin_api_mcp)

## Примечания

Требует API ключ CoinMarketCap, который можно получить на сайте CoinMarketCap. API ключ можно предоставить как переменную окружения или аргумент командной строки. Лицензировано под MIT License.