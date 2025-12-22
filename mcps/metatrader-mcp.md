---
title: MetaTrader MCP сервер
description: Мост, который соединяет AI-ассистентов с торговой платформой MetaTrader 5,
  позволяя пользователям выполнять сделки, управлять позициями и получать рыночные данные
  с помощью команд на естественном языке.
tags:
- Finance
- API
- AI
- Integration
- Analytics
author: Community
featured: false
---

Мост, который соединяет AI-ассистентов с торговой платформой MetaTrader 5, позволяя пользователям выполнять сделки, управлять позициями и получать рыночные данные с помощью команд на естественном языке.

## Установка

### PyPI

```bash
pip install metatrader-mcp-server
```

### HTTP сервер

```bash
metatrader-http-server --login YOUR_LOGIN --password YOUR_PASSWORD --server YOUR_SERVER --host 0.0.0.0 --port 8000
```

### Из исходного кода

```bash
git clone https://github.com/ariadng/metatrader-mcp-server.git
cd metatrader-mcp-server
pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "metatrader": {
      "command": "metatrader-mcp-server",
      "args": [
        "--login",    "YOUR_MT5_LOGIN",
        "--password", "YOUR_MT5_PASSWORD",
        "--server",   "YOUR_MT5_SERVER"
      ]
    }
  }
}
```

### Claude Desktop с пользовательским путем

```json
{
  "mcpServers": {
    "metatrader": {
      "command": "metatrader-mcp-server",
      "args": [
        "--login",    "YOUR_MT5_LOGIN",
        "--password", "YOUR_MT5_PASSWORD",
        "--server",   "YOUR_MT5_SERVER",
        "--path",     "C:\\Program Files\\MetaTrader 5\\terminal64.exe"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_account_info` | Получить баланс, эквити, прибыль, уровень маржи, кредитное плечо, валюту |
| `get_symbols` | Список всех доступных торговых символов |
| `get_symbol_price` | Получить текущую цену bid/ask для символа |
| `get_candles_latest` | Получить последние свечи (данные OHLCV) |
| `get_candles_by_date` | Получить исторические свечи за период |
| `place_market_order` | Выполнить мгновенные BUY/SELL ордера |
| `place_pending_order` | Разместить лимитные/стоп ордера для будущего исполнения |
| `modify_position` | Обновить стоп лосс или тейк профит |
| `get_all_positions` | Просмотреть все открытые позиции |
| `close_position` | Закрыть определенную позицию |
| `close_all_positions` | Закрыть все открытые позиции |
| `close_all_profitable_positions` | Закрыть только прибыльные сделки |
| `close_all_losing_positions` | Закрыть только убыточные сделки |
| `get_all_pending_orders` | Список всех отложенных ордеров |
| `cancel_pending_order` | Отменить определенный отложенный ордер |

## Возможности

- Торговля на естественном языке - общайтесь с AI на простом русском языке для выполнения сделок
- Поддержка множества AI - работает с Claude Desktop, ChatGPT (через Open WebUI) и другими
- Полный доступ к рынку - получайте цены в реальном времени, исторические данные и информацию о символах
- Полное управление счетом - проверяйте баланс, эквити, маржу и торговую статистику
- Управление ордерами - размещайте, изменяйте и закрывайте ордера простыми командами
- Безопасность - все учетные данные остаются на вашей машине
- Гибкие интерфейсы - используйте как MCP сервер или REST API

## Переменные окружения

### Обязательные
- `LOGIN` - номер логина MT5 счета
- `PASSWORD` - пароль MT5 счета
- `SERVER` - имя MT5 сервера (например, MetaQuotes-Demo)

### Опциональные
- `PATH` - пользовательский путь к терминалу MT5 (определяется автоматически, если не указан)

## Примеры использования

```
Show me my account balance
```

```
Buy 0.01 lots of EUR/USD
```

```
Close all profitable positions
```

```
What's the current price of EUR/USD?
```

```
Buy 0.01 lots of GBP/USD with stop loss at 1.2500 and take profit at 1.2700
```

## Ресурсы

- [GitHub Repository](https://github.com/ariadng/metatrader-mcp-server)

## Примечания

Требует установленный и запущенный терминал MetaTrader 5 с включенной алгоритмической торговлей. Работает как с демо, так и с реальными торговыми счетами. Торговля связана со значительными рисками - используйте ответственно.