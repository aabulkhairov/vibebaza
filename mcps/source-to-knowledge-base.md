---
title: Source to Knowledge Base MCP сервер
description: Преобразуйте репозитории с исходным кодом и контент Notion в доступные для поиска базы знаний с AI-поиском на GPT-5, умным разбиением на фрагменты и OpenAI embeddings для семантического понимания кода.
tags:
- Code
- AI
- Search
- Vector Database
- Productivity
author: Community
featured: false
---

Преобразуйте репозитории с исходным кодом и контент Notion в доступные для поиска базы знаний с AI-поиском на GPT-5, умным разбиением на фрагменты и OpenAI embeddings для семантического понимания кода.

## Установка

### NPM Global

```bash
npm install -g @vezlo/src-to-kb
```

### NPX

```bash
npx @vezlo/src-to-kb /path/to/repo
```

### Project Dependency

```bash
npm install @vezlo/src-to-kb
```

### From Source

```bash
git clone https://github.com/vezlo/src-to-kb.git
cd src-to-kb
npm install
```

## Возможности

- Поддержка исходного кода на множестве языков (JavaScript, TypeScript, Python, Java, C++, Go, Rust и др.)
- Интеграция с Notion для импорта страниц и баз данных
- Три режима ответов: End User (простой), Developer (технический), Copilot (ориентированный на код)
- REST API с документацией Swagger
- Умное разбиение кода на фрагменты с настраиваемым перекрытием
- OpenAI embeddings для семантического поиска
- Интеграция с внешним сервером для продакшн развертываний
- MCP сервер для интеграции с Claude Code и Cursor
- AI-поиск с использованием OpenAI GPT-5
- Опциональная аутентификация по API ключу

## Переменные окружения

### Опциональные
- `OPENAI_API_KEY` - Необходим для генерации embeddings и AI-поиска
- `NOTION_API_KEY` - Необходим для интеграции с Notion для импорта страниц и баз данных
- `EXTERNAL_KB_URL` - URL для интеграции с внешним сервером для отправки данных базы знаний
- `EXTERNAL_KB_API_KEY` - API ключ для аутентификации с внешним сервером базы знаний
- `API_KEY` - Опциональный API ключ для защиты REST API сервера
- `PORT` - Номер порта для REST API сервера (по умолчанию: 3000)

## Примеры использования

```
Generate knowledge base from source code: src-to-kb ./my-nextjs-app --output ./my-kb
```

```
Search codebase: src-to-kb-search search "How does routing work?" --mode developer
```

```
Import Notion content: src-to-kb --source=notion --notion-url=https://notion.so/Your-Page-abc123
```

```
Start MCP server: src-to-kb-mcp
```

```
Get codebase statistics: src-to-kb-search stats --kb ./project-kb
```

## Ресурсы

- [GitHub Repository](https://github.com/vezlo/src-to-kb)

## Примечания

Поддерживает интеграцию с внешним сервером с продакшн-готовым assistant-server для корпоративных развертываний. Включает инструмент автоконфигурации (src-to-kb-mcp-install) для настройки Claude Code и Cursor. Доступные команды включают src-to-kb (генерация), src-to-kb-search (поиск), src-to-kb-api (REST сервер) и src-to-kb-mcp (MCP сервер).