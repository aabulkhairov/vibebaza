---
title: Gemini Bridge MCP сервер
description: Легковесный MCP сервер, который позволяет ассистентам для программирования взаимодействовать с Google Gemini AI через официальный CLI, обеспечивая нулевые расходы на API и бесшовную интеграцию с Claude Code, Cursor, VS Code и другими MCP-совместимыми клиентами.
tags:
- AI
- Integration
- Code
- Productivity
- API
author: eLyiN
featured: false
install_command: claude mcp add gemini-bridge -s user -- uvx gemini-bridge
---

Легковесный MCP сервер, который позволяет ассистентам для программирования взаимодействовать с Google Gemini AI через официальный CLI, обеспечивая нулевые расходы на API и бесшовную интеграцию с Claude Code, Cursor, VS Code и другими MCP-совместимыми клиентами.

## Установка

### Установка через PyPI

```bash
pip install gemini-bridge
claude mcp add gemini-bridge -s user -- uvx gemini-bridge
```

### Из исходного кода

```bash
git clone https://github.com/shelakh/gemini-bridge.git
cd gemini-bridge
uvx --from build pyproject-build
pip install dist/*.whl
claude mcp add gemini-bridge -s user -- uvx gemini-bridge
```

### Установка для разработки

```bash
git clone https://github.com/shelakh/gemini-bridge.git
cd gemini-bridge
pip install -e .
claude mcp add gemini-bridge-dev -s user -- python -m src
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "gemini-bridge": {
      "command": "uvx",
      "args": ["gemini-bridge"],
      "env": {}
    }
  }
}
```

### VS Code

```json
{
  "servers": {
    "gemini-bridge": {
      "type": "stdio",
      "command": "uvx",
      "args": ["gemini-bridge"]
    }
  }
}
```

### С пользовательским таймаутом

```json
{
  "mcpServers": {
    "gemini-bridge": {
      "command": "uvx",
      "args": ["gemini-bridge"],
      "env": {
        "GEMINI_BRIDGE_TIMEOUT": "120"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `consult_gemini` | Прямой мост CLI для простых запросов к Gemini AI |
| `consult_gemini_with_files` | Мост CLI с вложенными файлами для детального анализа конкретных файлов |

## Возможности

- Прямая интеграция с Gemini CLI с нулевыми расходами на API
- Простые MCP инструменты для базовых запросов и анализа файлов
- Работа без состояния без сессий и кеширования
- Готовность к продакшену с надежной обработкой ошибок и 60-секундными таймаутами
- Минимальные зависимости требуют только mcp>=1.0.0 и Gemini CLI
- Универсальная совместимость с MCP для Claude Code, Cursor, VS Code и других клиентов
- Поддержка установки как через uvx, так и через традиционный pip

## Переменные окружения

### Опциональные
- `GEMINI_BRIDGE_TIMEOUT` - Настройка пользовательского таймаута для CLI операций (по умолчанию: 60 секунд)
- `GEMINI_BRIDGE_MAX_INLINE_TOTAL_BYTES` - Максимальное количество байт для встроенной передачи файлов

## Примеры использования

```
What authentication patterns are used in this codebase?
```

```
Review these auth files for security issues
```

```
Find authentication patterns in this codebase
```

```
Analyze these auth files and suggest improvements
```

```
Compare these database implementations and recommend the best approach
```

## Ресурсы

- [GitHub Repository](https://github.com/eLyiN/gemini-bridge)

## Примечания

Требует установки и аутентификации Google Gemini CLI (npm install -g @google/gemini-cli && gemini auth login). Поддерживает выбор модели между 'flash' и 'pro', с встроенным режимом для небольших файлов и at_command режимом для операций с более крупными файлами. Включает защиту размера файлов с ограничениями ~256 KB на файл и ~512 KB на запрос.