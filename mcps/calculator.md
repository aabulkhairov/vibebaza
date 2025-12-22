---
title: Calculator MCP сервер
description: MCP сервер, который позволяет языковым моделям выполнять точные численные вычисления с помощью инструмента калькулятора.
tags:
- Productivity
- API
author: githejie
featured: true
---

MCP сервер, который позволяет языковым моделям выполнять точные численные вычисления с помощью инструмента калькулятора.

## Установка

### uv (рекомендуется)

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### PIP

```bash
pip install mcp-server-calculator
```

### Запуск через модуль Python

```bash
python -m mcp_server_calculator
```

## Конфигурация

### uv (рекомендуется)

```json
"mcpServers": {
  "calculator": {
    "command": "uvx",
    "args": ["mcp-server-calculator"]
  }
}
```

### PIP

```json
"mcpServers": {
  "calculator": {
    "command": "python",
    "args": ["-m", "mcp_server_calculator"]
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `calculate` | Вычисляет/оценивает заданное выражение |

## Возможности

- Точные численные вычисления
- Оценка выражений
- Поддержка математических вычислений

## Ресурсы

- [GitHub Repository](https://github.com/githejie/mcp-server-calculator)

## Примечания

Лицензировано под лицензией MIT. Инструмент calculate требует параметр expression (строка, обязательный), который содержит математическое выражение для оценки.