---
title: Heurist Mesh Agent MCP сервер
description: Подключается к API Heurist Mesh для предоставления доступа к специализированным web3 AI агентам для анализа блокчейн данных, безопасности смарт-контрактов, метрик токенов и блокчейн взаимодействий.
tags:
- AI
- Finance
- API
- Security
- Analytics
author: Community
featured: false
---

Подключается к API Heurist Mesh для предоставления доступа к специализированным web3 AI агентам для анализа блокчейн данных, безопасности смарт-контрактов, метрик токенов и блокчейн взаимодействий.

## Установка

### UV (Рекомендуется)

```bash
git clone https://github.com/heurist-network/heurist-mesh-mcp-server.git
cd heurist-mesh-mcp-server
uv pip install -e .
```

### Docker

```bash
git clone https://github.com/heurist-network/heurist-mesh-mcp-server.git
cd heurist-mesh-mcp-server
docker build -t mesh-tool-server .
```

## Конфигурация

### Claude Desktop (UV)

```json
{
  "mcpServers": {
    "heurist-mesh-agent": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/heurist-mesh-mcp-server/mesh_mcp_server",
        "run",
        "mesh-tool-server"
      ],
      "env": {
        "HEURIST_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "mesh-agent": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "-e", "TRANSPORT=stdio",
        "-e", "HEURIST_API_KEY=your-api-key-here",
        "mesh-tool-server"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_coingecko_id` | Поиск токена по названию для получения его CoinGecko ID |
| `get_token_info` | Получение детальной информации о токене и рыночных данных используя CoinGecko ID |
| `get_trending_coins` | Получение текущих топовых трендовых криптовалют на CoinGecko |
| `get_specific_pair_info` | Получение информации о торговой паре по цепочке и адресу пары на DexScreener |
| `get_token_pairs` | Получение торговых пар по цепочке и адресу токена на DexScreener |
| `get_token_profiles` | Получение базовой информации о последних токенах из DexScreener |
| `search_pairs` | Поиск торговых пар на DexScreener по названию, символу или адресу токена |
| `get_trending_tokens` | Получение текущих трендовых токенов на Twitter |
| `search_account` | Анализ Twitter аккаунта с поиском упоминаний и статистикой аккаунта |
| `search_mentions` | Поиск упоминаний конкретных токенов или тем на Twitter |
| `answer` | Получение прямого ответа на вопрос используя API Exa |
| `search` | Поиск веб-страниц по запросу |
| `search_and_answer` | Выполнение операций поиска и получения ответа по запросу |
| `execute_search` | Выполнение веб-поиска с чтением веб-страниц |
| `generate_queries` | Генерация связанных поисковых запросов по теме для расширения исследования |

## Возможности

- Подключается к API Heurist Mesh
- Загружает инструменты для данных криптовалют и Web3 сценариев использования
- Поддерживает транспорты SSE и stdio
- Работает с Claude в Cursor, Claude Desktop и других MCP-совместимых интерфейсах
- Используйте один API ключ для доступа к нескольким сервисам (например, рыночные данные криптовалют CoinGecko, обзоры безопасности токенов GoPlus)
- Доступна размещенная конечная точка SSE
- Настраиваемый выбор агентов

## Переменные окружения

### Обязательные
- `HEURIST_API_KEY` - API ключ для доступа к сервисам Heurist Mesh

## Ресурсы

- [GitHub Repository](https://github.com/heurist-network/heurist-mesh-mcp-server)

## Примечания

Размещенная конечная точка SSE доступна по адресу https://sequencer-v2.heurist.xyz/mcp/sse. Вы можете настроить поддерживаемых агентов, отредактировав список DEFAULT_AGENTS в server.py. Бесплатные API кредиты доступны с пригласительным кодом 'claude'. Используйте портал Heurist Mesh MCP Portal (https://mcp.heurist.ai/) для создания SSE MCP серверов по требованию.