---
title: Excel MCP сервер
description: Model Context Protocol (MCP) сервер, который позволяет работать с Excel файлами без установки Microsoft Excel. Создавайте, читайте и изменяйте Excel книги с помощью вашего AI агента.
tags:
- Productivity
- Analytics
- Storage
author: Community
featured: false
---

Model Context Protocol (MCP) сервер, который позволяет работать с Excel файлами без установки Microsoft Excel. Создавайте, читайте и изменяйте Excel книги с помощью вашего AI агента.

## Установка

### UVX Stdio

```bash
uvx excel-mcp-server stdio
```

### UVX SSE

```bash
uvx excel-mcp-server sse
```

### UVX Streamable HTTP

```bash
uvx excel-mcp-server streamable-http
```

## Конфигурация

### Stdio Transport

```json
{
   "mcpServers": {
      "excel": {
         "command": "uvx",
         "args": ["excel-mcp-server", "stdio"]
      }
   }
}
```

### SSE Transport

```json
{
   "mcpServers": {
      "excel": {
         "url": "http://localhost:8000/sse",
      }
   }
}
```

### Streamable HTTP Transport

```json
{
   "mcpServers": {
      "excel": {
         "url": "http://localhost:8000/mcp",
      }
   }
}
```

## Возможности

- Операции с Excel: Создание, чтение, обновление книг и листов
- Манипуляция данными: Формулы, форматирование, графики, сводные таблицы и Excel таблицы
- Валидация данных: Встроенная проверка диапазонов, формул и целостности данных
- Форматирование: Стили шрифтов, цвета, границы, выравнивание и условное форматирование
- Операции с таблицами: Создание и управление Excel таблицами с пользовательскими стилями
- Создание графиков: Генерация различных типов графиков (линейные, столбчатые, круговые, точечные и др.)
- Сводные таблицы: Создание динамических сводных таблиц для анализа данных
- Управление листами: Легкое копирование, переименование, удаление листов
- Поддержка трех транспортов: stdio, SSE (устаревший), и streamable HTTP
- Удаленная и локальная работа: Работает как локально, так и в качестве удаленного сервиса

## Переменные окружения

### Опциональные
- `EXCEL_FILES_PATH` - Указывает серверу где читать и записывать Excel файлы (обязательно для SSE и Streamable HTTP транспортов, по умолчанию ./excel_files)
- `FASTMCP_PORT` - Управляет портом, который прослушивает сервер (по умолчанию 8017)

## Ресурсы

- [GitHub Repository](https://github.com/haris-musa/excel-mcp-server)

## Примечания

Полная документация по инструментам доступна в файле TOOLS.md. SSE транспорт является устаревшим. Для stdio протокола путь к файлу предоставляется с каждым вызовом инструмента, поэтому EXCEL_FILES_PATH не нужен.