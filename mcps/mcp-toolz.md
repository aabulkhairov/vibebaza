---
title: MCP Toolz MCP сервер
description: Система управления контекстом, сохранения задач и получения обратной связи от AI для Claude Code, которая сохраняет контексты и задачи между сессиями и предоставляет обратную связь от нескольких AI моделей (ChatGPT, Claude, Gemini, DeepSeek).
tags:
- Productivity
- AI
- Code
- Storage
- Integration
author: taylorleese
featured: false
---

Система управления контекстом, сохранения задач и получения обратной связи от AI для Claude Code, которая сохраняет контексты и задачи между сессиями и предоставляет обратную связь от нескольких AI моделей (ChatGPT, Claude, Gemini, DeepSeek).

## Установка

### PyPI

```bash
pip install mcp-toolz
```

### Из исходного кода

```bash
git clone https://github.com/taylorleese/mcp-toolz.git
cd mcp-toolz
python3 -m venv venv
source venv/bin/activate
pip install -e ".[dev]"
```

## Конфигурация

### Claude Code (pip install)

```json
{
  "mcpServers": {
    "mcp-toolz": {
      "command": "python",
      "args": ["-m", "mcp_server"],
      "env": {
        "OPENAI_API_KEY": "sk-...",
        "ANTHROPIC_API_KEY": "sk-ant-...",
        "GOOGLE_API_KEY": "...",
        "DEEPSEEK_API_KEY": "sk-..."
      }
    }
  }
}
```

### Claude Code (из исходного кода)

```json
{
  "mcpServers": {
    "mcp-toolz": {
      "command": "python",
      "args": ["-m", "mcp_server"],
      "cwd": "/absolute/path/to/mcp-toolz",
      "env": {
        "PYTHONPATH": "/absolute/path/to/mcp-toolz/src"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `context_save` | Сохранить новый контекст с автоматической информацией о сессии |
| `context_search` | Поиск контекстов по запросу или тегам |
| `context_get` | Получить контекст по ID |
| `context_list` | Показать список последних контекстов |
| `context_delete` | Удалить контекст по ID |
| `ask_chatgpt` | Получить анализ контекста от ChatGPT с пользовательскими вопросами |
| `ask_claude` | Получить анализ контекста от Claude с пользовательскими вопросами |
| `ask_gemini` | Получить анализ контекста от Gemini с пользовательскими вопросами |
| `ask_deepseek` | Получить анализ контекста от DeepSeek с пользовательскими вопросами |
| `todo_search` | Поиск снимков задач |
| `todo_get` | Получить задачу по ID |
| `todo_list` | Показать список последних задач |
| `todo_save` | Сохранить снимок задачи |
| `todo_restore` | Получить активный или определенный снимок задачи |
| `todo_delete` | Удалить задачу по ID |

## Возможности

- Непрерывность сессий - никогда не теряйте контекст при перезапуске Claude Code
- Организация проектов - контексты и задачи организованы по директориям проектов
- Отслеживание сессий с уникальными ID для каждой сессии Claude Code
- Обратная связь от AI через ChatGPT, Claude, Gemini и DeepSeek
- Множественные типы контекстов: разговоры, фрагменты кода, архитектурные предложения, трассировки ошибок
- Постоянные задачи, которые сохраняются и восстанавливаются между сессиями
- Полнотекстовый поиск по содержимому, тегам, проекту или сессии
- Доступ как через CLI, так и через MCP инструменты
- Автоматическая маркировка сессий с путем проекта и временными метками
- Общая база данных для доступа между сессиями и проектами

## Переменные окружения

### Опциональные
- `OPENAI_API_KEY` - API ключ для обратной связи от ChatGPT
- `ANTHROPIC_API_KEY` - API ключ для обратной связи от Claude
- `GOOGLE_API_KEY` - API ключ для обратной связи от Gemini
- `DEEPSEEK_API_KEY` - API ключ для обратной связи от DeepSeek
- `MCP_TOOLZ_DB_PATH` - Пользовательский путь для SQLite базы данных (для синхронизации между машинами)

## Примеры использования

```
I'm deciding between using Redis or Memcached for caching user sessions. Save this as a context and ask ChatGPT for their analysis. Use tags: caching, redis, memcached, architecture
```

```
Save my current todo list so I can restore it tomorrow
```

```
What was I working on yesterday? Restore my todos
```

```
I'm getting "TypeError: Cannot read property 'map' of undefined" in my React component. Save this as an error context and ask ChatGPT, Claude, and Gemini for debugging suggestions
```

```
Search my contexts for performance optimization ideas
```

## Ресурсы

- [GitHub Repository](https://github.com/taylorleese/mcp-toolz)

## Примечания

Требует Python 3.13+. Данные по умолчанию сохраняются в ~/.mcp-toolz/contexts.db и используются всеми проектами. Поддерживает MCP ресурсы для пассивного обнаружения контекстов и задач. Каждая сессия Claude Code получает автоматическое отслеживание с уникальными ID.