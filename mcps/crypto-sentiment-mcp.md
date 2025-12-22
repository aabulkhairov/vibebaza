---
title: crypto-sentiment-mcp сервер
description: MCP сервер, который предоставляет анализ настроений по криптовалютам для ИИ-агентов,
  используя агрегированные данные социальных сетей и новостей от Santiment для отслеживания рыночных настроений
  и обнаружения новых трендов.
tags:
- Finance
- Analytics
- API
- Monitoring
author: kukapay
featured: false
---

MCP сервер, который предоставляет анализ настроений по криптовалютам для ИИ-агентов, используя агрегированные данные социальных сетей и новостей от Santiment для отслеживания рыночных настроений и обнаружения новых трендов.

## Установка

### Из исходного кода

```bash
git clone https://github.com/kukapay/crypto-sentiment-mcp.git
cd crypto-sentiment-mcp
```

## Конфигурация

### MCP клиент

```json
{
  "mcpServers": {
    "crypto-sentiment-mcp": {
      "command": "uv",
      "args": ["--directory", "path/to/crypto-sentiment-mcp", "run", "main.py"],
      "env": {
        "SANTIMENT_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_sentiment_balance` | Получить средний баланс настроений для актива за указанный период |
| `get_social_volume` | Получить общее количество упоминаний в социальных сетях для актива |
| `alert_social_shift` | Обнаружить значительные всплески или падения в социальном объеме по сравнению с предыдущим средним значением |
| `get_trending_words` | Получить топ трендовых слов в криптодискуссиях, ранжированных по рейтингу за период |
| `get_social_dominance` | Измерить процент криптомедиа дискуссий, в которых доминирует актив |

## Возможности

- Анализ настроений: Получение баланса настроений (позитивные против негативных) для конкретных криптовалют
- Отслеживание социального объема: Мониторинг общих упоминаний в социальных сетях и обнаружение значительных изменений (всплески или падения)
- Социальное доминирование: Измерение доли дискуссий, которую занимает актив в криптомедиа
- Трендовые слова: Выявление самых популярных терминов, набирающих популярность в криптовалютных дискуссиях

## Переменные окружения

### Обязательные
- `SANTIMENT_API_KEY` - API ключ от Santiment для доступа к данным настроений по криптовалютам и социальным сетям

## Примеры использования

```
What's the sentiment balance for Bitcoin over the last week?
```

```
How many times has Ethereum been mentioned on social media in the past 5 days?
```

```
Tell me if there's been a big change in Bitcoin's social volume recently, with a 30% threshold.
```

```
What are the top 3 trending words in crypto over the past 3 days?
```

```
How dominant is Ethereum in social media discussions this week?
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/crypto-sentiment-mcp)

## Примечания

Требует Python 3.10 или выше и API ключ Santiment (бесплатный или платный) с app.santiment.net