---
title: mcp-memory-service MCP сервер
description: Production-ready MCP сервис памяти с нулевой блокировкой базы данных, гибридным бэкендом (быстрое локальное чтение + облачная синхронизация) и интеллектуальным поиском по памяти для AI-ассистентов. Включает автоконфигурацию для многоклиентского доступа, локальное чтение за 5мс с фоновой синхронизацией через Cloudflare, Natural Memory Triggers с точностью 85%+, и совместную работу через OAuth 2.1.
tags:
- AI
- Database
- Vector Database
- Storage
- Analytics
author: doobidoo
featured: true
---

Production-ready MCP сервис памяти с нулевой блокировкой базы данных, гибридным бэкендом (быстрое локальное чтение + облачная синхронизация) и интеллектуальным поиском по памяти для AI-ассистентов. Включает автоконфигурацию для многоклиентского доступа, локальное чтение за 5мс с фоновой синхронизацией через Cloudflare, Natural Memory Triggers с точностью 85%+, и совместную работу через OAuth 2.1.

## Установка

### PyPI

```bash
pip install mcp-memory-service
```

### UV

```bash
uv pip install mcp-memory-service
```

### Из исходников

```bash
git clone https://github.com/doobidoo/mcp-memory-service.git
cd mcp-memory-service && python install.py
```

### Docker

```bash
docker-compose up -d
```

### Smithery

```bash
npx -y @smithery/cli install @doobidoo/mcp-memory-service --client claude
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "memory": {
      "command": "memory",
      "args": ["server"],
      "env": {
        "MCP_MEMORY_STORAGE_BACKEND": "hybrid"
      }
    }
  }
}
```

## Возможности

- Нулевая блокировка базы данных с одновременным доступом
- Гибридный бэкенд с быстрым локальным чтением (5мс) и облачной синхронизацией
- Natural Memory Triggers с точностью 85%+
- Интеллектуальный поиск по памяти и автоматическое внедрение контекста
- Совместная работа команды через OAuth 2.1
- Система консолидации памяти с оценкой затухания, вдохновленной сновидениями
- Поддержка множества клиентов (Claude Desktop, VS Code, Cursor, Continue и 13+ AI-приложений)
- SQLite-vec с ONNX эмбеддингами для автономной работы
- Фоновая синхронизация через Cloudflare
- Интеграция контекста с учетом Git

## Переменные окружения

### Опциональные
- `MCP_MEMORY_STORAGE_BACKEND` - Тип бэкенда хранения (hybrid, cloudflare, sqlite)

## Ресурсы

- [GitHub Repository](https://github.com/doobidoo/mcp-memory-service)

## Примечания

Поддерживает Python 3.12+ (примечание о совместимости Python 3.13 для sqlite-vec). Пользователям macOS может понадобиться Homebrew Python для поддержки расширений SQLite. Первоначальная настройка включает автоматическое скачивание модели (~25MB). Функция видимого внедрения памяти показывает топ-3 воспоминания при запуске сессии с оценками релевантности.