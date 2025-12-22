---
title: obsidian-mcp сервер
description: MCP сервер, который позволяет AI-ассистентам взаимодействовать с хранилищами Obsidian, предоставляя инструменты для чтения, создания, редактирования и управления заметками и тегами.
tags:
- Productivity
- Storage
- Search
- Integration
author: StevenStevrakis
featured: true
---

MCP сервер, который позволяет AI-ассистентам взаимодействовать с хранилищами Obsidian, предоставляя инструменты для чтения, создания, редактирования и управления заметками и тегами.

## Установка

### NPX

```bash
npx -y obsidian-mcp /path/to/your/vault
```

### Smithery

```bash
npx -y @smithery/cli install obsidian-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/StevenStavrakis/obsidian-mcp
cd obsidian-mcp
npm install
npm run build
```

## Конфигурация

### Ручная установка Claude Desktop

```json
{
    "mcpServers": {
        "obsidian": {
            "command": "npx",
            "args": ["-y", "obsidian-mcp", "/path/to/your/vault", "/path/to/your/vault2"]
        }
    }
}
```

### Claude Desktop для разработки

```json
{
    "mcpServers": {
        "obsidian": {
            "command": "node",
            "args": ["<absolute-path-to-obsidian-mcp>/build/main.js", "/path/to/your/vault", "/path/to/your/vault2"]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `read-note` | Прочитать содержимое заметки |
| `create-note` | Создать новую заметку |
| `edit-note` | Редактировать существующую заметку |
| `delete-note` | Удалить заметку |
| `move-note` | Переместить заметку в другое место |
| `create-directory` | Создать новую директорию |
| `search-vault` | Искать заметки в хранилище |
| `add-tags` | Добавить теги к заметке |
| `remove-tags` | Удалить теги из заметки |
| `rename-tag` | Переименовать тег во всех заметках |
| `manage-tags` | Список и организация тегов |
| `list-available-vaults` | Список всех доступных хранилищ (помогает с мультихранилищными настройками) |

## Возможности

- Чтение и поиск заметок в вашем хранилище
- Создание новых заметок и директорий
- Редактирование существующих заметок
- Перемещение и удаление заметок
- Управление тегами (добавление, удаление, переименование)
- Поиск содержимого хранилища

## Ресурсы

- [GitHub Repository](https://github.com/StevenStavrakis/obsidian-mcp)

## Примечания

ВАЖНО: Этот MCP имеет доступ на чтение и запись к вашему хранилищу Obsidian. Сделайте резервную копию хранилища перед использованием. Требует Node.js 20 или выше. Файлы конфигурации: macOS: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: %APPDATA%\Claude\claude_desktop_config.json. Логи доступны по адресу: macOS: ~/Library/Logs/Claude/mcp*.log, Windows: %APPDATA%\Claude\logs\mcp*.log