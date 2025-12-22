---
title: Language Server MCP сервер
description: MCP сервер, который запускает и предоставляет языковой сервер для LLM, помогая клиентам с поддержкой MCP легче навигировать по кодовым базам, предоставляя им доступ к семантическим инструментам вроде получения определений, ссылок, переименования и диагностики.
tags:
- Code
- DevOps
- Productivity
- Integration
- API
author: isaacphi
featured: true
---

MCP сервер, который запускает и предоставляет языковой сервер для LLM, помогая клиентам с поддержкой MCP легче навигировать по кодовым базам, предоставляя им доступ к семантическим инструментам вроде получения определений, ссылок, переименования и диагностики.

## Установка

### Go Install

```bash
go install github.com/isaacphi/mcp-language-server@latest
```

### Из исходного кода

```bash
git clone https://github.com/isaacphi/mcp-language-server.git
cd mcp-language-server
```

## Конфигурация

### Claude Desktop - Go (gopls)

```json
{
  "mcpServers": {
    "language-server": {
      "command": "mcp-language-server",
      "args": ["--workspace", "/Users/you/dev/yourproject/", "--lsp", "gopls"],
      "env": {
        "PATH": "/opt/homebrew/bin:/Users/you/go/bin",
        "GOPATH": "/users/you/go",
        "GOCACHE": "/users/you/Library/Caches/go-build",
        "GOMODCACHE": "/Users/you/go/pkg/mod"
      }
    }
  }
}
```

### Claude Desktop - Rust (rust-analyzer)

```json
{
  "mcpServers": {
    "language-server": {
      "command": "mcp-language-server",
      "args": [
        "--workspace",
        "/Users/you/dev/yourproject/",
        "--lsp",
        "rust-analyzer"
      ]
    }
  }
}
```

### Claude Desktop - Python (pyright)

```json
{
  "mcpServers": {
    "language-server": {
      "command": "mcp-language-server",
      "args": [
        "--workspace",
        "/Users/you/dev/yourproject/",
        "--lsp",
        "pyright-langserver",
        "--",
        "--stdio"
      ]
    }
  }
}
```

### Claude Desktop - TypeScript

```json
{
  "mcpServers": {
    "language-server": {
      "command": "mcp-language-server",
      "args": [
        "--workspace",
        "/Users/you/dev/yourproject/",
        "--lsp",
        "typescript-language-server",
        "--",
        "--stdio"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `definition` | Получает полный исходный код определения любого символа (функция, тип, константа и т.д.) из... |
| `references` | Находит все использования и ссылки символа по всей кодовой базе |
| `diagnostics` | Предоставляет диагностическую информацию для конкретного файла, включая предупреждения и ошибки |
| `hover` | Отображает документацию, подсказки типов или другую информацию при наведении для указанной позиции |
| `rename_symbol` | Переименовывает символ по всему проекту |
| `edit_file` | Позволяет вносить множественные текстовые правки в файл на основе номеров строк. Обеспечивает более надежный и к... |

## Возможности

- Поддерживает множественные языковые серверы (gopls, rust-analyzer, pyright, typescript-language-server, clangd)
- Языковой сервер должен взаимодействовать через stdio
- Аргументы после -- отправляются как аргументы языковому серверу
- Переменные окружения передаются языковому серверу
- Семантическая навигация и анализ кода
- Переименование символов в рамках проекта
- Редактирование файлов с операциями на основе номеров строк

## Переменные окружения

### Опциональные
- `PATH` - Должен содержать путь к go и к gopls (для Go проектов)
- `GOPATH` - Путь к Go рабочему пространству (для Go проектов)
- `GOCACHE` - Директория кэша сборки Go (для Go проектов)
- `GOMODCACHE` - Директория кэша модулей Go (для Go проектов)
- `LOG_LEVEL` - Установите в DEBUG для включения подробного логирования в stderr для всех компонентов

## Ресурсы

- [GitHub Repository](https://github.com/isaacphi/mcp-language-server)

## Примечания

Это бета-версия программного обеспечения. Кодовая база использует отредактированный код из gopls для обработки LSP коммуникации и использует mcp-go для MCP коммуникации. Включен justfile для удобства разработки. Поддерживает тестирование снимков для локальной разработки с mock рабочими пространствами.