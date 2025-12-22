---
title: Open-Sourced MCP Servers Directory MCP сервер
description: Веб-сайт каталога для поиска и просмотра крутых MCP серверов с возможностью живого предпросмотра и курируемой коллекцией.
tags:
- Directory
- Web
- Database
- Integration
- Productivity
author: chatmcp
featured: true
---

Веб-сайт каталога для поиска и просмотра крутых MCP серверов с возможностью живого предпросмотра и курируемой коллекцией.

## Установка

### Из исходного кода

```bash
git clone https://github.com/chatmcp/mcp-directory.git
cd mcp-directory
pnpm install
```

## Возможности

- Живой предпросмотр каталога MCP серверов
- Интеграция с базой данных Supabase
- Веб-интерфейс для просмотра MCP серверов
- Сообществом управляемый каталог крутых MCP серверов

## Переменные окружения

### Обязательные
- `SUPABASE_URL` - URL базы данных Supabase для хранения данных
- `SUPABASE_ANON_KEY` - Анонимный ключ Supabase для доступа к базе данных
- `NEXT_PUBLIC_WEB_URL` - Публичный URL для веб-приложения

## Ресурсы

- [GitHub Repository](https://github.com/chatmcp/mcp-directory)

## Примечания

Это веб-приложение каталога для MCP серверов, а не сам MCP сервер. Требует настройки базы данных Supabase и выполнения SQL файла из data/install.sql. Живая версия доступна по адресу https://mcp.so. Поддержка сообщества доступна через каналы Telegram, Discord и Twitter.