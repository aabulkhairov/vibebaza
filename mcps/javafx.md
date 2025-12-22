---
title: JavaFX MCP сервер
description: Этот MCP сервер позволяет большим языковым моделям (LLM) создавать рисунки с использованием примитивов JavaFX через реализацию на основе Quarkus.
tags:
- Media
- Code
- Productivity
- Integration
author: quarkiverse
featured: true
---

Этот MCP сервер позволяет большим языковым моделям (LLM) создавать рисунки с использованием примитивов JavaFX через реализацию на основе Quarkus.

## Установка

### JBang

```bash
jbang jfx@quarkiverse/quarkus-mcp-servers
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "jfx": {
      "command": "jbang",
      "args": [
        "jfx@quarkiverse/quarkus-mcp-servers"
      ]
    }
  }
}
```

## Возможности

- Создание рисунков с использованием примитивов JavaFX
- Интеграция с большими языковыми моделями
- Реализация MCP сервера на основе Quarkus
- Распространение через JBang для простой установки

## Ресурсы

- [GitHub Repository](https://github.com/quarkiverse/quarkus-mcp-servers)

## Примечания

Компиляция в нативный исполняемый файл в данный момент не поддерживается из-за зависимостей JavaFX, хотя это должно быть возможно с использованием GluonFX. Сервер требует предварительной установки JBang. Изначальная реализация принадлежит @konczdev.