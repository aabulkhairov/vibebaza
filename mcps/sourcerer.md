---
title: Sourcerer MCP сервер
description: MCP сервер для семантического поиска и навигации по коду, который помогает AI агентам работать эффективно, обеспечивая концептуальный поиск по кодовой базе без необходимости чтения целых файлов, что значительно сокращает использование токенов.
tags:
- Code
- AI
- Search
- Vector Database
- Productivity
author: Community
featured: false
install_command: claude mcp add sourcerer -e OPENAI_API_KEY=your-openai-api-key -e
  SOURCERER_WORKSPACE_ROOT=$(pwd) -- sourcerer
---

MCP сервер для семантического поиска и навигации по коду, который помогает AI агентам работать эффективно, обеспечивая концептуальный поиск по кодовой базе без необходимости чтения целых файлов, что значительно сокращает использование токенов.

## Установка

### Go

```bash
go install github.com/st3v3nmw/sourcerer-mcp/cmd/sourcerer@latest
```

### Homebrew

```bash
brew tap st3v3nmw/tap
brew install st3v3nmw/tap/sourcerer
```

## Конфигурация

### mcp.json

```json
{
  "mcpServers": {
    "sourcerer": {
      "command": "sourcerer",
      "env": {
        "OPENAI_API_KEY": "your-openai-api-key",
        "SOURCERER_WORKSPACE_ROOT": "/path/to/your/project"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `semantic_search` | Поиск релевантного кода с помощью семантического поиска |
| `get_chunk_code` | Получение определенных фрагментов по ID |
| `find_similar_chunks` | Поиск похожих фрагментов |
| `index_workspace` | Ручной запуск переиндексации |
| `get_index_status` | Проверка прогресса индексации |

## Возможности

- Использует Tree-sitter для парсинга исходных файлов в AST и извлечения значимых фрагментов кода
- Отслеживает изменения файлов с помощью fsnotify и учитывает файлы .gitignore
- Генерирует эмбеддинги через OpenAI API для семантического поиска по сходству
- Сохраняет постоянную векторную базу данных в директории .sourcerer/db/
- Обеспечивает концептуальный поиск, а не просто текстовое сопоставление
- Автоматически переиндексирует измененные файлы
- Предоставляет стабильные ID фрагментов в формате: file.ext::Type::method

## Переменные окружения

### Обязательные
- `OPENAI_API_KEY` - Необходим для генерации эмбеддингов
- `SOURCERER_WORKSPACE_ROOT` - Путь к директории вашего проекта

## Ресурсы

- [GitHub Repository](https://github.com/st3v3nmw/sourcerer-mcp)

## Примечания

Требует Git репозиторий, учитывает файлы .gitignore, добавьте .sourcerer/ в .gitignore. В настоящее время поддерживает Go, JavaScript, Markdown, Python, TypeScript. Планируется поддержка C, C++, Java, Ruby, Rust и других языков.