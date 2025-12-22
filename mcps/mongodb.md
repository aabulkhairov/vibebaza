---
title: MongoDB MCP сервер
description: MCP сервер, который позволяет LLM взаимодействовать с базами данных MongoDB, предоставляя возможности для анализа схем коллекций и выполнения операций MongoDB через стандартизированный интерфейс.
tags:
- Database
- Analytics
- Integration
- Productivity
author: Community
featured: false
install_command: npx -y @smithery/cli install mcp-mongo-server --client claude
---

MCP сервер, который позволяет LLM взаимодействовать с базами данных MongoDB, предоставляя возможности для анализа схем коллекций и выполнения операций MongoDB через стандартизированный интерфейс.

## Установка

### NPX

```bash
npm install -g mcp-mongo-server
```

### Из исходного кода

```bash
git clone https://github.com/kiliczsh/mcp-mongo-server.git
cd mcp-mongo-server
npm install
npm run build
```

### Docker

```bash
docker build -t mcp-mongo-server .
docker run -it -d -e MCP_MONGODB_URI="mongodb://muhammed:kilic@localhost:27017/database" -e MCP_MONGODB_READONLY="true" mcp-mongo-server
```

### Smithery

```bash
npx -y @smithery/cli install mcp-mongo-server --client claude
```

### mcp-get

```bash
npx @michaellatman/mcp-get@latest install mcp-mongo-server
```

## Конфигурация

### Claude Desktop - аргументы команды

```json
{
  "mcpServers": {
    "mongodb": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-mongo-server",
        "mongodb://muhammed:kilic@localhost:27017/database"
      ]
    }
  }
}
```

### Claude Desktop - переменные окружения

```json
{
  "mcpServers": {
    "mongodb": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-mongo-server"
      ],
      "env": {
        "MCP_MONGODB_URI": "mongodb://muhammed:kilic@localhost:27017/database"
      }
    }
  }
}
```

### Конфигурация Windsurf

```json
{
  "mcpServers": {
    "mongodb": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-mongo-server",
        "mongodb://muhammed:kilic@localhost:27017/database"
      ]
    }
  }
}
```

### Конфигурация Cursor

```json
{
  "mcpServers": {
    "mongodb": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-mongo-server",
        "mongodb://muhammed:kilic@localhost:27017/database"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `query` | Выполнение MongoDB запросов с опциональным анализом плана выполнения |
| `aggregate` | Запуск пайплайнов агрегации с опциональным планированием запросов |
| `count` | Подсчет документов, соответствующих критериям |
| `update` | Изменение документов в коллекциях |
| `insert` | Добавление новых документов в коллекции |
| `createIndex` | Создание индексов коллекций |
| `serverInfo` | Получение деталей MongoDB сервера и отладочной информации |

## Возможности

- Умная обработка ObjectId с настраиваемыми режимами конвертации
- Режим только для чтения для безопасного доступа к продакшн базам данных
- Анализ и вывод схем коллекций
- Анализ планов выполнения для оптимизации запросов
- Поддержка пайплайнов агрегации
- Создание и управление индексами
- Автодополнение коллекций для улучшенного взаимодействия с LLM
- Гибкая конфигурация через переменные окружения или опции командной строки
- Предпочтение вторичного чтения для оптимальной производительности в режиме только для чтения

## Переменные окружения

### Опциональные
- `MCP_MONGODB_URI` - URI подключения к MongoDB
- `MCP_MONGODB_READONLY` - Включает режим только для чтения, когда установлено в 'true'

## Примеры использования

```
Найти всех пользователей старше 30 с их именами и email
```

```
Посчитать все электронные товары в инвентаре
```

```
Получить общие продажи по клиентам используя агрегацию
```

```
Обновить заголовок поста по ID
```

```
Вставить новые комментарии в коллекцию комментариев
```

## Ресурсы

- [GitHub Repository](https://github.com/kiliczsh/mcp-mongo-server)

## Примечания

Поддерживает несколько режимов конвертации ObjectId (auto, none, force). Используйте MCP Inspector для отладки с помощью 'npm run inspector'. Включает поддержку оценки с пакетом mcp-eval. Совместим с редакторами Claude Desktop, Windsurf и Cursor.