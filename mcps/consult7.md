---
title: consult7 MCP сервер
description: MCP сервер, который позволяет AI агентам консультироваться с моделями большого контекстного окна через OpenRouter для анализа обширных коллекций файлов, целых кодовых баз и репозиториев документов, которые превышают текущие лимиты контекста агента.
tags:
- Code
- AI
- API
- Analytics
- Integration
author: Community
featured: false
install_command: claude mcp add -s user consult7 uvx -- consult7 your-openrouter-api-key
---

MCP сервер, который позволяет AI агентам консультироваться с моделями большого контекстного окна через OpenRouter для анализа обширных коллекций файлов, целых кодовых баз и репозиториев документов, которые превышают текущие лимиты контекста агента.

## Установка

### Claude Code

```bash
claude mcp add -s user consult7 uvx -- consult7 your-openrouter-api-key
```

### UVX напрямую

```bash
uvx consult7 <api-key> [--test]
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "consult7": {
      "type": "stdio",
      "command": "uvx",
      "args": ["consult7", "your-openrouter-api-key"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `consultation` | Консультируется с моделями большого контекста для анализа файлов с указанным запросом, моделью и режимом рассуждения |

## Возможности

- Анализ целых кодовых баз в одном запросе с использованием моделей до 2M токенов контекста
- Поддержка 500+ моделей через OpenRouter, включая GPT-5.1, Gemini 3 Pro, Claude 4.5 и Grok 4
- Три режима производительности: быстрый (без рассуждений), средний (умеренные рассуждения), думающий (максимум рассуждений)
- Сопоставление шаблонов файлов с подстановочными знаками в именах файлов
- Опциональное сохранение выходных файлов для предотвращения переполнения контекста агента
- Быстрые мнемоники для популярных комбинаций модель+режим (gemt, gptt, grot, gemf, ULTRA)
- Динамические лимиты размера файлов на основе контекстных окон модели
- Автоматическая фильтрация чувствительных файлов и директорий

## Переменные окружения

### Обязательные
- `OPENROUTER_API_KEY` - API ключ для сервиса OpenRouter для доступа к различным AI моделям

## Примеры использования

```
Summarize the architecture and main components of this Python project
```

```
Analyze the authentication flow across this codebase and suggest security improvements
```

```
Generate a comprehensive code review report with architecture analysis and recommendations
```

```
Explain the main architecture of these source files
```

```
Find security vulnerabilities in this codebase and think step by step about improvements
```

## Ресурсы

- [GitHub Repository](https://github.com/szeider/consult7)

## Примечания

Требует API ключ OpenRouter. Поддерживает быстрые мнемоники типа 'gemt' для Gemini 3 Pro + думающий режим, 'ULTRA' для параллельного выполнения через несколько передовых моделей. Пути к файлам должны быть абсолютными с подстановочными знаками только в именах файлов, а не в путях директорий.