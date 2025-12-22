---
title: Postman MCP сервер
description: MCP сервер для запуска коллекций Postman с помощью Newman, позволяющий LLM выполнять API тесты и получать детальные результаты через стандартизированный интерфейс.
tags:
- API
- DevOps
- Monitoring
- Productivity
author: Community
featured: false
---

MCP сервер для запуска коллекций Postman с помощью Newman, позволяющий LLM выполнять API тесты и получать детальные результаты через стандартизированный интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-postman --client claude
```

### Из исходного кода

```bash
git clone <repository-url>
cd mcp-postman
pnpm install
pnpm build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "postman-runner": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-postman/build/index.js"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `run-collection` | Запускает коллекцию Postman и возвращает результаты тестирования, включая общий статус успеха/неудачи, ... |

## Возможности

- Запуск коллекций Postman с помощью Newman
- Поддержка файлов окружения
- Поддержка глобальных переменных
- Детальные результаты тестирования, включая общий статус успеха/неудачи
- Сводка по тестам (общее количество, пройденные, неудачные)
- Подробная информация об ошибках
- Временные характеристики выполнения

## Примеры использования

```
Run the Postman collection at /path/to/collection.json and tell me if all tests passed
```

## Ресурсы

- [GitHub Repository](https://github.com/shannonlal/mcp-postman)

## Примечания

Сервер поддерживает запуск коллекций с опциональными файлами окружения, файлами глобальных переменных и настраиваемым количеством итераций. Результаты тестирования включают в себя полную информацию о времени выполнения и детали ошибок для отладки API тестов.