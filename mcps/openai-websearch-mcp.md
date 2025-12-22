---
title: OpenAI WebSearch MCP сервер
description: Продвинутый MCP сервер, который предоставляет интеллектуальные возможности веб-поиска
  с использованием reasoning моделей OpenAI, с поддержкой новейшей серии GPT-5 и умным
  контролем усилий для различных случаев использования.
tags:
- Search
- AI
- Web Scraping
- API
- Integration
author: ConechoAI
featured: false
---

Продвинутый MCP сервер, который предоставляет интеллектуальные возможности веб-поиска с использованием reasoning моделей OpenAI, с поддержкой новейшей серии GPT-5 и умным контролем усилий для различных случаев использования.

## Установка

### Установка в один клик

```bash
OPENAI_API_KEY=sk-xxxx uvx --with openai-websearch-mcp openai-websearch-mcp-install
```

### uvx (Рекомендуется)

```bash
# Установить и запустить напрямую
uvx openai-websearch-mcp

# Или установить глобально
uvx install openai-websearch-mcp
```

### pip

```bash
# Установить из PyPI
pip install openai-websearch-mcp

# Запустить сервер
python -m openai_websearch_mcp
```

### Из исходного кода

```bash
# Клонировать репозиторий
git clone https://github.com/yourusername/openai-websearch-mcp.git
cd openai-websearch-mcp

# Установить зависимости
uv sync

# Запустить в режиме разработки
uv run python -m openai_websearch_mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "openai-websearch-mcp": {
      "command": "uvx",
      "args": ["openai-websearch-mcp"],
      "env": {
        "OPENAI_API_KEY": "your-api-key-here",
        "OPENAI_DEFAULT_MODEL": "gpt-5-mini"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "openai-websearch-mcp": {
      "command": "uvx",
      "args": ["openai-websearch-mcp"],
      "env": {
        "OPENAI_API_KEY": "your-api-key-here",
        "OPENAI_DEFAULT_MODEL": "gpt-5-mini"
      }
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "openai-websearch-mcp": {
      "command": "/path/to/your/project/.venv/bin/python",
      "args": ["-m", "openai_websearch_mcp"],
      "env": {
        "OPENAI_API_KEY": "your-api-key-here",
        "OPENAI_DEFAULT_MODEL": "gpt-5-mini",
        "PYTHONPATH": "/path/to/your/project/src"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `openai_web_search` | Интеллектуальный веб-поиск с поддержкой reasoning моделей, поддерживающий параметры для ввода запроса, модель... |

## Возможности

- Полная совместимость с новейшими reasoning моделями OpenAI (gpt-5, gpt-5-mini, gpt-5-nano, o3, o4-mini)
- Интеллектуальные значения по умолчанию для reasoning_effort в зависимости от случая использования
- Многорежимный поиск: быстрые итерации с gpt-5-mini или глубокие исследования с gpt-5
- Поддержка кастомизации поиска на основе местоположения
- Полная документация параметров для простой интеграции
- Поддержка переменных окружения для легкого деплоя

## Переменные окружения

### Обязательные
- `OPENAI_API_KEY` - Ваш API ключ OpenAI

### Опциональные
- `OPENAI_DEFAULT_MODEL` - Модель по умолчанию для использования

## Примеры использования

```
Найти последние разработки в области AI reasoning моделей, используя openai_web_search
```

```
Использовать openai_web_search с gpt-5 и высоким reasoning усилием для предоставления всестороннего анализа прорывов в квантовых вычислениях
```

```
Найти локальные tech митапы в Сан-Франциско на этой неделе, используя openai_web_search
```

## Ресурсы

- [GitHub Repository](https://github.com/ConechoAI/openai-websearch-mcp)

## Примечания

Поддерживает как быстрые поиски с gpt-5-mini для быстрых итераций, так и глубокие исследования с gpt-5 для всестороннего анализа. Сервер автоматически обрабатывает совместимость, применяя reasoning параметры только к совместимым моделям. Используйте MCP Inspector для отладки: `npx @modelcontextprotocol/inspector uvx openai-websearch-mcp`