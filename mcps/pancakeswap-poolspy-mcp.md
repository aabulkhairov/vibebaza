---
title: pancakeswap-poolspy-mcp сервер
description: MCP сервер, который отслеживает новые пулы ликвидности на PancakeSwap,
  предоставляя данные в реальном времени для DeFi аналитиков, трейдеров и разработчиков.
tags:
- Finance
- Analytics
- Monitoring
- API
author: kukapay
featured: false
install_command: npx -y @smithery/cli install @kukapay/pancakeswap-poolspy-mcp --client
  claude
---

MCP сервер, который отслеживает новые пулы ликвидности на PancakeSwap, предоставляя данные в реальном времени для DeFi аналитиков, трейдеров и разработчиков.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @kukapay/pancakeswap-poolspy-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/kukapay/pancakeswap-poolspy-mcp.git
cd pancakeswap-poolspy-mcp
uv add mcp[cli] httpx dotenv
```

### Режим разработки

```bash
mcp dev main.py
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "PancakeSwap-PoolSpy": {
      "command": "uv",
      "args": ["--directory", "path/to/pancakeswap-poolspy-mcp", "run", "main.py"],
      "env": {
        "THEGRAPH_API_KEY": "your api key from The Graph"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_new_pools_bsc` | Получает список новых пулов PancakeSwap на BNB Smart Chain с настраиваемым временным диапазоном... |

## Возможности

- Отслеживание пулов в реальном времени: Получает пулы, созданные в указанном временном диапазоне (по умолчанию: 5 минут)
- Настраиваемые запросы: Позволяет изменить временной диапазон (в секундах) и количество возвращаемых пулов (по умолчанию: 100)
- Подробная метрика: Включает адрес пула, токены, временную метку создания, номер блока, количество транзакций, объем (USD) и общую заблокированную стоимость (USD)

## Переменные окружения

### Обязательные
- `THEGRAPH_API_KEY` - API ключ от The Graph для доступа к субграфу PancakeSwap

## Примеры использования

```
list newly created PancakeSwap pools from the last 1 hours
```

```
Display PancakeSwap pools created within the last 2 minutes
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/pancakeswap-poolspy-mcp)

## Примечания

Требуется Python 3.10+ и API ключ от The Graph. Сервер обеспечивает отслеживание новых пулов ликвидности в реальном времени с подробной метрикой, включая TVL, объем и данные транзакций.