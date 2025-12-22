---
title: claude-faf-mcp MCP сервер
description: Официальный MCP сервер для .FAF (Foundational AI-context Format), обеспечивающий постоянный контекст проекта с более чем 50 инструментами для оценки готовности к AI, анализа проектов и управления контекстом.
tags:
- AI
- Productivity
- Code
- Analytics
- Integration
author: Community
featured: false
---

Официальный MCP сервер для .FAF (Foundational AI-context Format), обеспечивающий постоянный контекст проекта с более чем 50 инструментами для оценки готовности к AI, анализа проектов и управления контекстом.

## Установка

### NPM Global

```bash
npm install -g claude-faf-mcp
```

### Desktop Extension

```bash
Download .mcpb file from: https://github.com/Wolfe-Jam/claude-faf-mcp/releases/latest
```

## Конфигурация

### Claude Desktop

```json
{"mcpServers": {"faf": {"command": "npx", "args": ["-y", "claude-faf-mcp"]}}}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `faf_quick` | Молниеносное создание project.faf (в среднем 3мс) |
| `faf_enhance` | Интеллектуальное улучшение с автоопределением |
| `faf_read` | Парсинг и валидация FAF файлов |
| `faf_write` | Создание/обновление FAF с валидацией |
| `faf_score` | Движок оценки готовности к AI |
| `faf_compress` | Интеллектуальная оптимизация размера |

## Возможности

- 51 MCP инструмент (100% автономные)
- Зарегистрированный IANA стандарт с официальным MIME типом: application/vnd.faf+yaml
- В 16.2 раза быстрее производительность по сравнению с CLI версиями благодаря прямым вызовам функций
- 19мс среднее время выполнения для всех встроенных команд
- Система оценки готовности к AI с ранжированием по уровням
- Нулевые зависимости со встроенным движком
- Универсальный протокол AI контекста для кроссплатформенной совместимости
- 14 встроенных команд без утечек памяти

## Примеры использования

```
Create a project.faf file for my current project
```

```
Score my project's AI-readiness
```

```
Enhance my existing project.faf with auto-detection
```

```
Validate and parse my FAF file
```

```
Optimize the size of my project context
```

## Ресурсы

- [GitHub Repository](https://github.com/Wolfe-Jam/claude-faf-mcp)

## Примечания

FAF позиционируется как фундаментальный, универсальный базовый слой для любой модели, использующей MCP Protocol. Файл project.faf живет в корне проекта между package.json и README.md, обеспечивая постоянный контекст проекта, который работает в Claude, Gemini, Codex и любой LLM.