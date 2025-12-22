---
title: commands MCP сервер
description: MCP сервер, который позволяет LLM выполнять терминальные команды напрямую,
  обеспечивая взаимодействие с системой через операции командной строки.
tags:
- DevOps
- Code
- Productivity
- Security
- Integration
author: Community
featured: false
---

MCP сервер, который позволяет LLM выполнять терминальные команды напрямую, обеспечивая взаимодействие с системой через операции командной строки.

## Установка

### NPX (Опубликованный пакет)

```bash
npx mcp-server-commands
```

### Из исходного кода

```bash
npm install
npm run build
```

### HTTP через mcpo

```bash
uvx mcpo --port 3010 --api-key "supersecret" -- npx mcp-server-commands
```

## Конфигурация

### Claude Desktop (Опубликованный пакет)

```json
{
  "mcpServers": {
    "mcp-server-commands": {
      "command": "npx",
      "args": ["mcp-server-commands"]
    }
  }
}
```

### Claude Desktop (Локальная сборка)

```json
{
  "mcpServers": {
    "mcp-server-commands": {
      "command": "/path/to/mcp-server-commands/build/index.js"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `run_command` | Выполняет терминальные команды типа hostname, ls -al, echo и т.д. Возвращает STDOUT и STDERR в виде текста с... |

## Возможности

- Выполнение любых терминальных команд
- Возвращает как STDOUT, так и STDERR
- Опциональный параметр stdin для интерактивных команд
- Передача кода интерпретаторам (fish, bash, zsh, python)
- Создание файлов с использованием stdin с командами типа cat
- Работает с Claude Sonnet 3.5 и Groq Desktop
- Совместим с локальными моделями через Ollama

## Примеры использования

```
hostname
```

```
ls -al
```

```
echo "hello world"
```

```
Pass code in stdin to commands like fish, bash, zsh, python
```

```
Create files with cat >> foo/bar.txt from text in stdin
```

## Ресурсы

- [GitHub Repository](https://github.com/g0t4/mcp-server-commands)

## Примечания

⚠️ ПРЕДУПРЕЖДЕНИЕ БЕЗОПАСНОСТИ: Будьте очень осторожны с командами, которые вы разрешаете выполнять этому серверу. Используйте 'Approve Once' в Claude Desktop для проверки каждой команды. Не запускайте с привилегиями sudo. Разрешения определяются пользователем, запускающим сервер. Совместим с Open-WebUI через мост mcpo. Логи доступны по адресу ~/Library/Logs/Claude/mcp-server-mcp-server-commands.log. Добавьте флаг --verbose для детального логирования.