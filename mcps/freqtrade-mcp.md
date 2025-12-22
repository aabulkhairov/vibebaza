---
title: freqtrade-mcp сервер
description: MCP сервер, который интегрируется с криптовалютным торговым ботом Freqtrade через его REST API, обеспечивая бесшовное взаимодействие с AI агентами для автоматизированных торговых операций.
tags:
- Finance
- API
- Integration
- Analytics
- Monitoring
author: kukapay
featured: false
---

MCP сервер, который интегрируется с криптовалютным торговым ботом Freqtrade через его REST API, обеспечивая бесшовное взаимодействие с AI агентами для автоматизированных торговых операций.

## Установка

### Клонирование и установка

```bash
git clone https://github.com/kukapay/freqtrade-mcp.git
cd freqtrade-mcp
pip install freqtrade-client mcp[cli]
```

### С UV

```bash
git clone https://github.com/kukapay/freqtrade-mcp.git
cd freqtrade-mcp
uv add freqtrade-client "mcp[cli]"
```

## Конфигурация

### Конфигурация MCP клиента

```json
"mcpServers": {
  "freqtrade-mcp": {
    "command": "uv",
    "args": [
      "--directory", "/your/path/to/freqtrade-mcp",
      "run",
      "__main__.py"
    ],
    "env": {
       "FREQTRADE_API_URL": "http://127.0.0.1:8080",
       "FREQTRADE_USERNAME": "your_username",
       "FREQTRADE_PASSWORD": "your_password"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `fetch_market_data` | Получение OHLCV данных для торговой пары |
| `fetch_bot_status` | Получение статуса открытых сделок |
| `fetch_profit` | Получение сводки по прибыли |
| `fetch_balance` | Получение баланса аккаунта |
| `fetch_performance` | Получение метрик производительности |
| `fetch_whitelist` | Получение белого списка пар |
| `fetch_blacklist` | Получение черного списка пар |
| `fetch_trades` | Получение истории сделок |
| `fetch_config` | Получение конфигурации бота |
| `fetch_locks` | Получение торговых блокировок |
| `place_trade` | Размещение покупки/продажи |
| `start_bot` | Запуск бота |
| `stop_bot` | Остановка бота |
| `reload_config` | Перезагрузка конфигурации бота |
| `add_blacklist` | Добавление пары в черный список |

## Возможности

- Получение рыночных данных в реальном времени (OHLCV) для торговых пар
- Мониторинг статуса бота и открытых сделок
- Получение сводок по прибыли и метрик производительности
- Управление балансом аккаунта и историей торговли
- Контроль белого/черного списка торговых пар
- Программное размещение сделок купли/продажи
- Запуск/остановка операций торгового бота
- Управление торговыми блокировками и конфигурацией
- Полная интеграция с REST API Freqtrade

## Переменные окружения

### Обязательные
- `FREQTRADE_API_URL` - URL эндпоинта REST API Freqtrade
- `FREQTRADE_USERNAME` - Имя пользователя для аутентификации в API Freqtrade
- `FREQTRADE_PASSWORD` - Пароль для аутентификации в API Freqtrade

## Примеры использования

```
Покажи мне почасовые данные цены для BTC/USDT
```

```
Какой текущий статус моих открытых сделок?
```

```
Сколько прибыли я получил до сих пор?
```

```
Каков мой баланс аккаунта?
```

```
Купи 0.01 BTC/USDT прямо сейчас
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/freqtrade-mcp)

## Примечания

Требует запущенный экземпляр Freqtrade с включенным REST API. Необходим Python 3.13+. Freqtrade должен быть настроен с включенным api_server и правильными учетными данными для аутентификации.