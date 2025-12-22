---
title: Rust MCP Filesystem MCP сервер
description: Молниеносно быстрый, асинхронный и легковесный MCP сервер, написанный на Rust для эффективной обработки различных файловых операций, обеспечивающий улучшенную производительность по сравнению с JavaScript альтернативами.
tags:
- Storage
- Code
- Productivity
- DevOps
author: rust-mcp-stack
featured: true
---

Молниеносно быстрый, асинхронный и легковесный MCP сервер, написанный на Rust для эффективной обработки различных файловых операций, обеспечивающий улучшенную производительность по сравнению с JavaScript альтернативами.

## Установка

### Shell скрипт

```bash
curl --proto '=https' --tlsv1.2 -LsSf https://github.com/rust-mcp-stack/rust-mcp-filesystem/releases/download/v0.3.8/rust-mcp-filesystem-installer.sh | sh
```

### PowerShell скрипт

```bash
powershell -ExecutionPolicy Bypass -c "irm https://github.com/rust-mcp-stack/rust-mcp-filesystem/releases/download/v0.3.8/rust-mcp-filesystem-installer.ps1 | iex"
```

### Homebrew

```bash
brew install rust-mcp-stack/tap/rust-mcp-filesystem
```

### NPM

```bash
npm i -g @rustmcp/rust-mcp-filesystem@latest
```

### Docker

```bash
https://hub.docker.com/mcp/server/rust-mcp-filesystem
```

## Возможности

- Высокая производительность: Написан на Rust для скорости и эффективности, использует асинхронный ввод/вывод
- Только чтение по умолчанию: Запускается без доступа на запись, обеспечивая безопасность до явной настройки
- Продвинутый поиск по шаблонам: Поддерживает полное сопоставление glob-паттернов для точной фильтрации файлов
- Поддержка MCP Roots: Позволяет клиентам динамически изменять разрешенные директории
- Поддержка ZIP архивов: Инструменты для создания и извлечения ZIP архивов
- Легковесность: Автономный без внешних зависимостей, скомпилированный в один бинарный файл

## Ресурсы

- [GitHub Repository](https://github.com/rust-mcp-stack/rust-mcp-filesystem)

## Примечания

Это полная переписка на Rust проекта @modelcontextprotocol/server-filesystem. Документация доступна по адресу https://rust-mcp-stack.github.io/rust-mcp-filesystem. Также доступен в MCP Registry на Docker Hub. Создан с использованием rust-mcp-sdk и rust-mcp-schema.