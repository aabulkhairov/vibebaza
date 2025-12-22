---
title: CRASH MCP сервер
description: Продвинутый MCP сервер, который обеспечивает структурированное итеративное рассуждение для решения сложных задач с гибкой валидацией, отслеживанием уверенности, механизмами ревизии и поддержкой ветвления.
tags:
- AI
- Productivity
- Code
- Analytics
author: Community
featured: false
install_command: claude mcp add crash -- npx -y crash-mcp
---

Продвинутый MCP сервер, который обеспечивает структурированное итеративное рассуждение для решения сложных задач с гибкой валидацией, отслеживанием уверенности, механизмами ревизии и поддержкой ветвления.

## Установка

### NPM

```bash
npm install crash-mcp
```

### NPX

```bash
npx crash-mcp
```

### Docker

```bash
docker build -t crash-mcp .
docker run -i --rm crash-mcp
```

### Bun

```bash
bunx -y crash-mcp
```

### Deno

```bash
deno run --allow-env=NO_DEPRECATION,TRACE_DEPRECATION,MAX_HISTORY_SIZE,CRASH_STRICT_MODE,CRASH_OUTPUT_FORMAT,CRASH_NO_COLOR --allow-net npm:crash-mcp
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "crash": {
      "command": "npx",
      "args": ["-y", "crash-mcp"]
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "crash": {
      "command": "npx",
      "args": ["-y", "crash-mcp"],
      "env": {
        "MAX_HISTORY_SIZE": "100",
        "CRASH_STRICT_MODE": "false",
        "CRASH_OUTPUT_FORMAT": "console",
        "CRASH_NO_COLOR": "false"
      }
    }
  }
}
```

### VS Code

```json
"mcp": {
  "servers": {
    "crash": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "crash-mcp"]
    }
  }
}
```

### Windsurf

```json
{
  "mcpServers": {
    "crash": {
      "command": "npx",
      "args": ["-y", "crash-mcp"],
      "env": {
        "MAX_HISTORY_SIZE": "100",
        "CRASH_STRICT_MODE": "false",
        "CRASH_OUTPUT_FORMAT": "console"
      }
    }
  }
}
```

## Возможности

- Гибкие типы целей: Расширенный набор, включающий валидацию, исследование, гипотезы, коррекцию, планирование, плюс пользовательские цели
- Поток естественного языка: Никаких принудительных префиксов или жёсткого форматирования (настраивается)
- Механизм ревизии: Исправление и улучшение предыдущих шагов рассуждения
- Поддержка ветвления: Исследование нескольких путей решения параллельно
- Отслеживание уверенности: Выражение неопределённости с оценками уверенности (шкала 0-1)
- Структурированные действия: Улучшенная интеграция инструментов с параметрами и ожидаемыми результатами
- Управление сессиями: Несколько одновременных цепочек рассуждений с уникальными ID
- Множественные форматы вывода: Консольное, JSON и Markdown форматирование
- Строгий режим: Совместимость с оригинальной жёсткой валидацией
- Гибкий режим: Полный доступ к улучшенным функциям (по умолчанию)

## Переменные окружения

### Опциональные
- `MAX_HISTORY_SIZE` - Максимальный размер истории рассуждений
- `CRASH_STRICT_MODE` - Включить строгий режим для совместимости с предыдущими версиями
- `CRASH_OUTPUT_FORMAT` - Формат вывода (console, JSON, markdown)
- `CRASH_NO_COLOR` - Отключить цветной вывод

## Примеры использования

```
use crash to solve complex problems
```

```
Use CRASH for systematic analysis when sequential thinking or plan mode falls short
```

```
Apply CRASH when an agent can't solve an issue in one shot
```

## Ресурсы

- [GitHub Repository](https://github.com/nikkoxgonzales/crash-mcp)

## Примечания

CRASH v2.0 эффективен по токенам и упрощён по сравнению с последовательным мышлением. Он не включает коды в мысли и не требует от агентов перечисления всех доступных инструментов. Требует Node.js >= v18.0.0. Совместим с Cursor, Claude Code, VSCode, Windsurf и многими другими MCP клиентами.