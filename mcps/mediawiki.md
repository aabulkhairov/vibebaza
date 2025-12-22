---
title: MediaWiki MCP сервер
description: MCP (Model Context Protocol) сервер, который позволяет клиентам больших языковых моделей (LLM) взаимодействовать с любой MediaWiki вики, предоставляя инструменты для чтения, создания, редактирования и управления вики-страницами и файлами.
tags:
- Web Scraping
- API
- Productivity
- Search
- Integration
author: ProfessionalWiki
featured: false
install_command: claude mcp add mediawiki-mcp-server npx @professional-wiki/mediawiki-mcp-server@latest
---

MCP (Model Context Protocol) сервер, который позволяет клиентам больших языковых моделей (LLM) взаимодействовать с любой MediaWiki вики, предоставляя инструменты для чтения, создания, редактирования и управления вики-страницами и файлами.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @ProfessionalWiki/mediawiki-mcp-server --client claude
```

### NPX

```bash
npx @professional-wiki/mediawiki-mcp-server@latest
```

### VS Code команда

```bash
code --add-mcp '{"name":"mediawiki-mcp-server","command":"npx","args":["@professional-wiki/mediawiki-mcp-server@latest"]}'
```

### Claude Code

```bash
claude mcp add mediawiki-mcp-server npx @professional-wiki/mediawiki-mcp-server@latest
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mediawiki-mcp-server": {
      "command": "npx",
      "args": [
        "@professional-wiki/mediawiki-mcp-server@latest"
      ],
      "env": {
        "CONFIG": "path/to/config.json"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "mediawiki-mcp-server": {
      "command": "npx",
      "args": [
        "@professional-wiki/mediawiki-mcp-server@latest"
      ],
      "env": {
        "CONFIG": "path/to/config.json"
      }
    }
  }
}
```

### Windsurf

```json
{
  "mcpServers": {
    "mediawiki-mcp-server": {
      "command": "npx",
      "args": [
        "@professional-wiki/mediawiki-mcp-server@latest"
      ],
      "env": {
        "CONFIG": "path/to/config.json"
      }
    }
  }
}
```

### Claude Code

```json
"mcpServers": {
  "mediawiki-mcp-server": {
    "type": "stdio",
    "command": "npx",
    "args": [
      "@professional-wiki/mediawiki-mcp-server@latest"
    ],
    "env": {
      "CONFIG": "path/to/config.json"
    }
  }
},
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `add-wiki` | Добавляет новую вики как MCP ресурс по URL |
| `create-page` | Создать новую вики-страницу (требует аутентификации) |
| `delete-page` | Удалить вики-страницу (требует аутентификации) |
| `get-category-members` | Получить всех участников категории |
| `get-file` | Возвращает стандартный объект файла для файловой страницы |
| `get-page` | Возвращает стандартный объект страницы для вики-страницы |
| `get-page-history` | Возвращает информацию о последних ревизиях вики-страницы |
| `get-revision` | Возвращает стандартный объект ревизии для страницы |
| `remove-wiki` | Удаляет ресурс вики |
| `search-page` | Поиск по названиям и содержимому вики-страниц по заданным поисковым терминам |
| `search-page-by-prefix` | Выполнить поиск названий страниц по префиксу |
| `set-wiki` | Устанавливает ресурс вики для использования в текущей сессии |
| `undelete-page` | Восстановить вики-страницу (требует аутентификации) |
| `update-page` | Обновить существующую вики-страницу (требует аутентификации) |
| `upload-file` | Загружает файл в вики с локального диска (требует аутентификации) |

## Возможности

- Подключение к любой MediaWiki вики
- Поиск вики-страниц по названию и содержимому
- Получение содержимого страниц и истории ревизий
- Создание, обновление и удаление вики-страниц (с аутентификацией)
- Загрузка файлов с локального диска или веб-URL (с аутентификацией)
- Получение участников категорий и объектов файлов
- Поддержка как OAuth2 токенов, так и аутентификации по имени пользователя/паролю
- Динамическое управление ресурсами вики
- Поддержка приватных вики

## Переменные окружения

### Опциональные
- `CONFIG` - Путь к вашему файлу конфигурации
- `MCP_TRANSPORT` - Тип транспорта MCP сервера (stdio или http)
- `PORT` - Порт, используемый для StreamableHTTP транспорта

## Ресурсы

- [GitHub репозиторий](https://github.com/ProfessionalWiki/MediaWiki-MCP-Server)

## Примечания

Конфигурация требуется только при взаимодействии с приватными вики или использовании инструментов с аутентификацией. OAuth2 токены предпочтительнее аутентификации по имени пользователя/паролю. Для поддержки OAuth2 на вики должно быть установлено расширение OAuth. Операции с аутентификацией требуют специфических разрешений MediaWiki.