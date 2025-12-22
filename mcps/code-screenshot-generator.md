---
title: Code Screenshot Generator MCP сервер
description: MCP сервер, который позволяет Claude генерировать скриншоты кода с подсветкой синтаксиса и профессиональными темами, поддерживает чтение файлов, выбор строк, визуализацию git diff и пакетную обработку.
tags:
- Code
- Media
- Productivity
- DevOps
author: Community
featured: false
install_command: claude mcp add code-screenshot-mcp
---

MCP сервер, который позволяет Claude генерировать скриншоты кода с подсветкой синтаксиса и профессиональными темами, поддерживает чтение файлов, выбор строк, визуализацию git diff и пакетную обработку.

## Установка

### NPM Global

```bash
npm install -g code-screenshot-mcp
```

### Из исходников

```bash
git clone https://github.com/MoussaabBadla/code-screenshot-mcp.git
cd code-screenshot-mcp
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "code-screenshot": {
      "command": "code-screenshot-mcp"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate_code_screenshot` | Генерация скриншота из строки кода с подсветкой синтаксиса и темами |
| `screenshot_from_file` | Создание скриншота кода из файла с автоматическим определением языка и выбором диапазона строк |
| `screenshot_git_diff` | Генерация скриншота git diff для staged или unstaged изменений |
| `batch_screenshot` | Обработка нескольких файлов в одной операции для создания множественных скриншотов |

## Возможности

- 5 профессиональных тем: Dracula, Nord, Monokai, GitHub Light, GitHub Dark
- Интеграция с файлами: создание скриншотов кода напрямую из путей файлов с выбором диапазона строк
- Поддержка Git Diff: визуализация staged или unstaged изменений
- Пакетная обработка: одновременная обработка нескольких файлов
- Автоматическое определение языка: поддержка 20+ языков программирования
- Нативная интеграция с Claude: работает с Claude Desktop и Claude Code

## Примеры использования

```
Generate a code screenshot of this TypeScript function with Nord theme
```

```
Screenshot src/index.ts with Dracula theme
```

```
Screenshot lines 20-45 of src/generator.ts with Monokai theme
```

```
Screenshot my git diff with GitHub Dark theme
```

```
Screenshot src/index.ts, src/generator.ts, and src/templates.ts
```

## Ресурсы

- [GitHub Repository](https://github.com/MoussaabBadla/code-screenshot-mcp)

## Примечания

Поддерживает 20+ расширений файлов, включая .js, .jsx, .ts, .tsx, .py, .rb, .go, .rs, .java, .c, .cpp, .cs, .php, .swift, .kt, .sql, .sh, .yml, .yaml, .json, .xml, .html, .css, .scss, .md. Создан с использованием Playwright и Highlight.js.