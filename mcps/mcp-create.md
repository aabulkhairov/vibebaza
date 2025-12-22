---
title: MCP Create MCP сервер
description: Динамический сервис управления MCP серверами, который создает, запускает и управляет серверами Model Context Protocol как дочерними процессами, обеспечивая гибкую MCP экосистему.
tags:
- DevOps
- Code
- Integration
- Productivity
- API
author: tesla0225
featured: false
---

Динамический сервис управления MCP серверами, который создает, запускает и управляет серверами Model Context Protocol как дочерними процессами, обеспечивая гибкую MCP экосистему.

## Установка

### Docker

```bash
# Build Docker image
docker build -t mcp-create .

# Run Docker container
docker run -it --rm mcp-create
```

### Из исходного кода

```bash
# Clone repository
git clone https://github.com/tesla0225/mcp-create.git
cd mcp-create

# Install dependencies
npm install

# Build
npm run build

# Run
npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mcp-create": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "mcp-create"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create-server-from-template` | Создать MCP сервер из шаблона |
| `execute-tool` | Выполнить инструмент на сервере |
| `get-server-tools` | Получить список инструментов сервера |
| `delete-server` | Удалить сервер |
| `list-servers` | Получить список запущенных серверов |

## Возможности

- Динамическое создание и выполнение кода MCP сервера
- Поддержка только TypeScript (поддержка JavaScript и Python запланирована в будущих релизах)
- Выполнение инструментов на дочерних MCP серверах
- Обновление кода сервера и перезапуски
- Удаление ненужных серверов

## Примеры использования

```
Создать новый TypeScript MCP сервер из шаблона
```

```
Выполнить echo инструмент на определенном сервере с сообщением
```

```
Показать список всех запущенных серверов
```

```
Получить доступные инструменты с определенного сервера
```

```
Удалить ненужный сервер
```

## Ресурсы

- [GitHub Repository](https://github.com/tesla0225/mcp-create)

## Примечания

Docker — рекомендуемый способ запуска этого сервиса. Требует Node.js 18 или выше. Соображения безопасности включают ограничения выполнения кода, лимиты ресурсов, мониторинг процессов и валидацию путей для предотвращения атак с обходом каталогов. Лицензия MIT.