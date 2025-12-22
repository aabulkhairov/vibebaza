---
title: Ton Blockchain MCP сервер
description: MCP сервер, который обеспечивает взаимодействие с блокчейном TON на естественном языке для анализа торговли, выявления трендов, форензики и проверок соответствия.
tags:
- Finance
- Analytics
- API
- Security
author: devonmojito
featured: false
---

MCP сервер, который обеспечивает взаимодействие с блокчейном TON на естественном языке для анализа торговли, выявления трендов, форензики и проверок соответствия.

## Установка

### Из исходного кода

```bash
git clone https://github.com/devonmojito/ton-blockchain-mcp.git
cd ton-blockchain-mcp
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers":
    {
        "ton-mcp-server":
        {
            "command": "/Users/devon/ton-mcp/ton-blockchain-mcp/venv/bin/python",
            "args":
            [
                "-m",
                "tonmcp.mcp_server"
            ],
            "cwd": "/Users/devon/ton-mcp/ton-blockchain-mcp/src",
            "env":
            {
                "PYTHONPATH": "/Users/devon/ton-mcp/ton-blockchain-mcp/src"
            },
            "stdio": true
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `analyze_address` | Анализирует TON адрес для получения баланса, холдингов жеттонов, NFT и недавней активности с дополнительными... |
| `get_transaction_details` | Получает детали и анализ конкретной транзакции в блокчейне TON по её хешу |
| `find_hot_trends` | Находит трендовые токены, пулы или аккаунты в блокчейне TON за указанный период времени и категорию |
| `analyze_trading_patterns` | Анализирует торговые паттерны для TON адреса за указанный период времени, включая торговую активность... |
| `get_ton_price` | Получает текущую цену TON в режиме реального времени в указанной валюте с последними изменениями цены |
| `get_jetton_price` | Получает текущую цену и последние изменения для указанных жеттон токенов в заданной валюте |

## Возможности

- Обработка естественного языка для сложных блокчейн запросов на простом русском языке
- Анализ торговли, включая паттерны, прибыльность и стратегии
- Выявление горячих трендов для трендовых токенов, активных пулов и аккаунтов с высокой активностью
- Форензика и соответствие для блокчейн расследований и проверок соответствия
- Доступ к данным в режиме реального времени через TON API

## Переменные окружения

### Обязательные
- `TON_API_KEY` - API ключ от TONAPI для доступа к данным блокчейна TON

## Примеры использования

```
What's the balance of address EQD1234...?
```

```
Find hot trading pairs in the last hour
```

```
Analyze trading patterns for this wallet
```

```
Show suspicious activity for address ABC
```

```
Trace money flow from this address
```

## Ресурсы

- [GitHub Repository](https://github.com/devonmojito/ton-blockchain-mcp)

## Примечания

⚠️ ВНИМАНИЕ: Этот проект находится в стадии бета-тестирования. Не доверяйте никаким цифрам, предоставляемым LLM моделью. Ничто в этом проекте не является финансовым советом. Используйте на свой страх и риск. Требует Python 3.10+ и TON API ключ от TONAPI.