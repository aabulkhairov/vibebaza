---
title: MCPShell MCP сервер
description: Инструмент, который позволяет LLM безопасно выполнять команды командной строки через Model Context Protocol (MCP), предоставляя защищенный мост между LLM и командами операционной системы с определениями инструментов на основе конфигурации и ограничениями безопасности.
tags:
- DevOps
- Security
- Code
- Productivity
- Integration
author: inercia
featured: false
---

Инструмент, который позволяет LLM безопасно выполнять команды командной строки через Model Context Protocol (MCP), предоставляя защищенный мост между LLM и командами операционной системы с определениями инструментов на основе конфигурации и ограничениями безопасности.

## Установка

### Go Run

```bash
go run github.com/inercia/MCPShell@v0.1.8 mcp --tools /my/example.yaml --logfile /some/path/mcpshell/example.log
```

## Конфигурация

### Cursor

```json
{
    "mcpServers": {
        "mcp-cli-examples": {
            "command": "go",
            "args": [
               "run", "github.com/inercia/MCPShell@v0.1.8",
               "mcp", "--tools", "/my/example.yaml",
               "--logfile", "/some/path/mcpshell/example.log"
            ]
        }
    }
}
```

### Cursor (Относительные пути)

```json
{
    "mcpServers": {
        "mcp-cli-examples": {
            "command": "go",
            "args": [
               "run", "github.com/inercia/MCPShell@v0.1.8",
               "mcp", "--tools", "example",
               "--logfile", "/some/path/mcpshell/example.log"
            ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `disk_usage` | Проверка использования диска для директории с настраиваемым анализом глубины |

## Возможности

- Гибкое выполнение команд с подстановкой параметров через шаблоны
- Определения инструментов на основе конфигурации в YAML с параметрами, ограничениями и форматированием вывода
- Безопасность через ограничения с использованием CEL выражений для валидации параметров
- Опциональные изолированные окружения для выполнения команд
- Быстрое прототипирование MCP инструментов путем добавления shell кода
- Режим агента для прямого подключения к LLM без отдельного MCP клиента
- Поддержка интерактивных диалогов и одноразового выполнения
- Опции развертывания в контейнерах и Kubernetes

## Примеры использования

```
I'm running out of space in my hard disk. Could you help me finding the problem?
```

```
Help me analyze disk usage to identify what's consuming space
```

## Ресурсы

- [GitHub Repository](https://github.com/inercia/mcpshell)

## Примечания

Поддерживает множество LLM клиентов (Cursor, VSCode, Witsy). Включает примеры для интеграции с kubectl и AWS CLI. Сильный акцент на безопасности - рекомендуется ограничивать инструменты только действиями для чтения и использовать ограничения для предотвращения инъекций команд. Директория инструментов по умолчанию: ~/.mcpshell/tools/. Конфигурация поддерживает относительные пути и может опускать расширения .yaml.