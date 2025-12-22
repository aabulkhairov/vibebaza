---
title: Large File MCP сервер
description: MCP сервер для интеллектуальной работы с большими файлами с умной разбивкой на части, навигацией и потоковой передачей. Включает LRU кэширование, поиск по regex и эффективную обработку файлов любого размера.
tags:
- Storage
- Code
- Productivity
- Analytics
- DevOps
author: willianpinho
featured: false
install_command: claude mcp add --transport stdio --scope user large-file-mcp -- npx
  -y @willianpinho/large-file-mcp
---

MCP сервер для интеллектуальной работы с большими файлами с умной разбивкой на части, навигацией и потоковой передачей. Включает LRU кэширование, поиск по regex и эффективную обработку файлов любого размера.

## Установка

### NPM Global

```bash
npm install -g @willianpinho/large-file-mcp
```

### NPX

```bash
npx @willianpinho/large-file-mcp
```

### Из исходного кода

```bash
git clone https://github.com/willianpinho/large-file-mcp.git
cd large-file-mcp
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "large-file": {
      "command": "npx",
      "args": ["-y", "@willianpinho/large-file-mcp"]
    }
  }
}
```

### Claude Desktop с переменными окружения

```json
{
  "mcpServers": {
    "large-file": {
      "command": "npx",
      "args": ["-y", "@willianpinho/large-file-mcp"],
      "env": {
        "CHUNK_SIZE": "1000",
        "CACHE_ENABLED": "true"
      }
    }
  }
}
```

### Gemini

```json
{
  "tools": [
    {
      "name": "large-file-mcp",
      "command": "npx @willianpinho/large-file-mcp",
      "protocol": "mcp"
    }
  ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `read_large_file_chunk` | Чтение определённого фрагмента большого файла с интеллектуальной разбивкой |
| `search_in_large_file` | Поиск по паттернам в больших файлах с контекстом и поддержкой regex |
| `get_file_structure` | Анализ структуры файла и получение подробных метаданных |
| `navigate_to_line` | Переход к определённой строке с окружающим контекстом |
| `get_file_summary` | Получение подробной статистической сводки по файлу |
| `stream_large_file` | Потоковая передача файла по частям для обработки очень больших файлов |

## Возможности

- Умная разбивка на части с автоматическим определением размера на основе типа файла
- Интеллектуальная навигация к определённым строкам с окружающим контекстом
- Мощный поиск по regex с контекстными строками до/после совпадений
- Комплексный анализ файлов с метаданными и статистическим анализом
- Эффективная работа с памятью при потоковой обработке файлов любого размера
- Оптимизированная производительность с встроенным LRU кэшированием
- Безопасная типизация с реализацией на TypeScript
- Кроссплатформенная поддержка для Windows, macOS и Linux

## Переменные окружения

### Опциональные
- `CHUNK_SIZE` - Количество строк по умолчанию на фрагмент
- `OVERLAP_LINES` - Перекрытие между фрагментами
- `MAX_FILE_SIZE` - Максимальный размер файла в байтах
- `CACHE_SIZE` - Размер кэша в байтах
- `CACHE_TTL` - Время жизни кэша в миллисекундах
- `CACHE_ENABLED` - Включение/отключение кэширования

## Примеры использования

```
Прочитай первый фрагмент из /var/log/system.log
```

```
Найди все сообщения ERROR в /var/log/app.log
```

```
Покажи мне строку 1234 из /code/app.ts с контекстом
```

```
Получи структуру файла /data/sales.csv
```

```
Проанализируй /var/log/nginx/access.log и найди все ошибки 404
```

## Ресурсы

- [GitHub Repository](https://github.com/willianpinho/large-file-mcp)

## Примечания

Поддерживает интеллектуальное определение типа файлов с оптимизированными размерами фрагментов для различных типов файлов (text, code, CSV, JSON, XML и др.). Включает продвинутое кэширование с 80-90% попаданий и прогрессивную загрузку для файлов больше 1GB. Расположение конфигурационных файлов: macOS в ~/Library/Application Support/Claude/claude_desktop_config.json и Windows в %APPDATA%\Claude\claude_desktop_config.json.