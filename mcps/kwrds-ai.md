---
title: kwrds.ai MCP сервер
description: MCP сервер для kwrds.ai - инструменты исследования ключевых слов и SEO, предоставляющий анализ ключевых слов, данные SERP и возможности генерации контента.
tags:
- Search
- Analytics
- AI
- API
author: mkotsollaris
featured: false
---

MCP сервер для kwrds.ai - инструменты исследования ключевых слов и SEO, предоставляющий анализ ключевых слов, данные SERP и возможности генерации контента.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yourusername/kwrds-ai-mcp
cd kwrds-ai-mcp
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "kwrds-ai": {
      "command": "/ABSOLUTE/PATH/TO/kwrds-ai-mcp/venv/bin/python",
      "args": ["/ABSOLUTE/PATH/TO/kwrds-ai-mcp/run_server.py"],
      "env": {
        "KWRDS_AI_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `keyword_research` | Исследование ключевых слов с объемами и конкуренцией |
| `topic_research` | Исследование тем |
| `serp_analysis` | Анализ SERP и данные ранжирования |
| `people_also_ask` | Вопросы из блока "Похожие вопросы" |
| `ai_content_generation` | Генерация контента с помощью AI |
| `url_ranking_analysis` | Анализ ранжирования URL |
| `usage_statistics` | Статистика использования |

## Возможности

- Исследование ключевых слов с объемами и конкуренцией
- Исследование тем
- Анализ SERP и данные ранжирования
- Вопросы из блока "Похожие вопросы"
- Генерация контента с помощью AI
- Анализ ранжирования URL
- Статистика использования

## Переменные окружения

### Обязательные
- `KWRDS_AI_API_KEY` - API ключ для сервиса kwrds.ai

## Примеры использования

```
Find keywords for 'digital marketing' in the US
```

```
Get People Also Ask questions for 'SEO tools'
```

```
Generate an SEO outline for 'best laptops'
```

```
Get best keywords for 'best laptops 2025'
```

```
Get 7W1H for 'best AI tools'
```

## Ресурсы

- [GitHub Repository](https://github.com/mkotsollaris/kwrds_ai_mcp)

## Примечания

Требует Python 3.11+. API ключ должен быть получен от kwrds.ai. Замените абсолютные пути в конфигурации на ваши фактические пути к проекту.