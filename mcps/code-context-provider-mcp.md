---
title: code-context-provider-mcp сервер
description: MCP сервер, который предоставляет контекст кода и анализ для AI-ассистентов,
  извлекая структуру директорий и символы кода с помощью WebAssembly Tree-sitter парсеров
  без нативных зависимостей.
tags:
- Code
- AI
- Analytics
- Productivity
- DevOps
author: Community
featured: false
---

MCP сервер, который предоставляет контекст кода и анализ для AI-ассистентов, извлекая структуру директорий и символы кода с помощью WebAssembly Tree-sitter парсеров без нативных зависимостей.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @AB498/code-context-provider-mcp --client claude
```

### NPM Global

```bash
npm install -g code-context-provider-mcp
```

### Настройка для разработки

```bash
git clone https://github.com/your-username/code-context-provider-mcp.git
cd code-context-provider-mcp
npm install
npm run setup
```

## Конфигурация

### Windows

```json
{
  "mcpServers": {
    "code-context-provider-mcp": {
      "command": "cmd.exe",
      "args": [
        "/c",
        "npx",
        "-y",
        "code-context-provider-mcp@latest"
      ]
    }
  }
}
```

### MacOS/Linux

```json
{
  "mcpServers": {
    "code-context-provider-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "code-context-provider-mcp@latest"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_code_context` | Анализирует директорию и возвращает её структуру вместе с символами кода (функции, переменные, классы...) |

## Возможности

- Генерация структуры дерева директорий
- Анализ JavaScript/TypeScript и Python файлов
- Извлечение символов кода (функции, переменные, классы, импорты, экспорты)
- Совместимость с протоколом MCP для бесшовной интеграции с AI-ассистентами
- Поддержка фильтрации по шаблонам файлов
- Настраиваемая глубина анализа директорий
- Нулевые нативные зависимости благодаря WebAssembly Tree-sitter парсерам
- Автоматическая фильтрация анонимных функций

## Примеры использования

```
Analyze the directory structure of my project
```

```
Extract all functions and classes from my JavaScript files
```

```
Get code context for files matching specific patterns like *.js and *.py
```

```
Analyze only the top 2 levels of directories in my large project
```

## Ресурсы

- [GitHub Repository](https://github.com/AB498/code-context-provider-mcp)

## Примечания

Поддерживает JavaScript (.js), JSX (.jsx), TypeScript (.ts), TSX (.tsx) и Python (.py) файлы для анализа символов кода. Шаблоны файлов поддерживают glob паттерны с подстановочными символами, прямые расширения файлов и точные имена файлов. Параметр максимальной глубины помогает эффективно обрабатывать крупные проекты. Если загрузка WASM парсера не удалась во время установки, пользователи могут вручную выполнить: npx code-context-provider-mcp-setup