---
title: uniswap-poolspy-mcp MCP сервер
description: MCP сервер, который отслеживает новосозданные пулы ликвидности на Uniswap в девяти блокчейн-сетях (Ethereum, Base, Optimism, Arbitrum, Polygon, BNB Smart Chain, Avalanche, Celo и Blast), предоставляя данные в реальном времени для DeFi аналитиков, трейдеров и разработчиков.
tags:
- Finance
- Monitoring
- Analytics
- API
author: kukapay
featured: false
---

MCP сервер, который отслеживает новосозданные пулы ликвидности на Uniswap в девяти блокчейн-сетях (Ethereum, Base, Optimism, Arbitrum, Polygon, BNB Smart Chain, Avalanche, Celo и Blast), предоставляя данные в реальном времени для DeFi аналитиков, трейдеров и разработчиков.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yourusername/uniswap-poolspy-mcp.git
cd uniswap-poolspy-mcp
curl -LsSf https://astral.sh/uv/install.sh | sh
uv sync
echo "THEGRAPH_API_KEY=your-api-key-here" > .env
```

### Запуск сервера

```bash
uv run main.py
```

### Режим разработки

```bash
uv run mcp dev main.py
```

### Установка MCP

```bash
uv run mcp install main.py --name "UniswapPoolSpy"
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "Uniswap-PoolSpy": {
      "command": "uv",
      "args": ["--directory", "path/to/uniswap-poolspy-mcp", "run", "main.py"],
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
| `get_new_pools` | Запрос новосозданных пулов ликвидности в указанных блокчейн-сетях с настраиваемыми параметрами... |

## Возможности

- Мониторинг создания пулов Uniswap V3 в 9 блокчейн-сетях
- Настраиваемый временной диапазон и ограничения результатов для запроса новых пулов
- Поддержка сортировки по времени, количеству транзакций, объему или TVL
- Данные в реальном времени для DeFi аналитиков, трейдеров и разработчиков

## Переменные окружения

### Обязательные
- `THEGRAPH_API_KEY` - API ключ от The Graph для доступа к данным блокчейна

## Примеры использования

```
Show me new pools on Ethereum from the last 10 minutes
```

```
List pools on Base sorted by volume, limit to 50
```

```
What pools were created on Polygon in the past hour, ordered by TVL?
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/uniswap-poolspy-mcp)

## Примечания

Требует Python 3.10+, менеджер пакетов uv и действующий API ключ The Graph. Поддерживает 9 блокчейн-сетей: Ethereum, Base, Optimism, Arbitrum, Polygon, BNB Smart Chain, Avalanche, Celo и Blast. Инструмент принимает параметры для выбора сети, сортировки (timestamp, txcount, volume, tvl), временного диапазона в секундах (по умолчанию: 300) и ограничений результатов (по умолчанию: 100).