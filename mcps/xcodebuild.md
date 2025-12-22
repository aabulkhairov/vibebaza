---
title: xcodebuild MCP сервер
description: MCP сервер для сборки iOS workspace/проектов, который обеспечивает бесшовный рабочий процесс при работе с iOS проектами в Visual Studio Code с использованием расширений типа Cline или Roo Code.
tags:
- DevOps
- Code
- Productivity
author: ShenghaiWang
featured: false
---

MCP сервер для сборки iOS workspace/проектов, который обеспечивает бесшовный рабочий процесс при работе с iOS проектами в Visual Studio Code с использованием расширений типа Cline или Roo Code.

## Установка

### uv (рекомендуется)

```bash
uvx mcpxcodebuild
```

### PIP

```bash
pip install mcpxcodebuild
python -m mcpxcodebuild
```

## Конфигурация

### Claude.app (используя uvx)

```json
{
  "mcpServers": {
    "mcpxcodebuild": {
      "command": "uvx",
      "args": ["mcpxcodebuild"]
    }
  }
}
```

### Claude.app (используя pip)

```json
{
  "mcpServers": {
    "mcpxcodebuild": {
      "command": "python",
      "args": ["-m", "mcpxcodebuild"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `build` | Сборка iOS Xcode workspace/проекта |
| `test` | Запуск тестов для iOS Xcode workspace/проекта |

## Возможности

- Сборка iOS Xcode workspace/проектов
- Запуск тестов для iOS проектов
- Бесшовная интеграция с расширениями Visual Studio Code типа Cline или Roo Code
- Передача ошибок в LLM для улучшенного рабочего процесса отладки

## Ресурсы

- [GitHub Repository](https://github.com/ShenghaiWang/xcodebuild)

## Примечания

Лицензирован под MIT License. Оба инструмента требуют параметр 'folder' (строка, обязательный), указывающий полный путь к текущей папке, где расположен iOS Xcode workspace/проект.