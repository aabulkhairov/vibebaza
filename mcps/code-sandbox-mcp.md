---
title: code-sandbox-mcp MCP сервер
description: Безопасная изолированная среда для выполнения кода в Docker контейнерах, предоставляющая AI приложениям изолированное и безопасное выполнение кода через контейнеризацию.
tags:
- Code
- DevOps
- Security
- Integration
author: Community
featured: false
---

Безопасная изолированная среда для выполнения кода в Docker контейнерах, предоставляющая AI приложениям изолированное и безопасное выполнение кода через контейнеризацию.

## Установка

### Быстрая установка (Linux/macOS)

```bash
curl -fsSL https://raw.githubusercontent.com/Automata-Labs-team/code-sandbox-mcp/main/install.sh | bash
```

### Быстрая установка (Windows)

```bash
irm https://raw.githubusercontent.com/Automata-Labs-team/code-sandbox-mcp/main/install.ps1 | iex
```

### Ручная установка

```bash
1. Download the latest release for your platform from the releases page
2. Place the binary in a directory in your PATH
3. Make it executable (Unix-like systems): chmod +x code-sandbox-mcp
```

## Конфигурация

### Claude Desktop (Linux)

```json
{
    "mcpServers": {
        "code-sandbox-mcp": {
            "command": "/path/to/code-sandbox-mcp",
            "args": [],
            "env": {}
        }
    }
}
```

### Claude Desktop (macOS)

```json
{
    "mcpServers": {
        "code-sandbox-mcp": {
            "command": "/path/to/code-sandbox-mcp",
            "args": [],
            "env": {}
        }
    }
}
```

### Claude Desktop (Windows)

```json
{
    "mcpServers": {
        "code-sandbox-mcp": {
            "command": "C:\\path\\to\\code-sandbox-mcp.exe",
            "args": [],
            "env": {}
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `sandbox_initialize` | Инициализирует новую вычислительную среду для выполнения кода с использованием указанного Docker образа |
| `copy_project` | Копирует директорию в файловую систему песочницы |
| `write_file` | Записывает файл в файловую систему песочницы |
| `sandbox_exec` | Выполняет команды в изолированной среде |
| `copy_file` | Копирует отдельный файл в файловую систему песочницы |
| `sandbox_stop` | Останавливает и удаляет работающий контейнер песочницы |

## Возможности

- Гибкое управление контейнерами: Создание и управление изолированными Docker контейнерами для выполнения кода
- Поддержка пользовательских окружений: Использование любого Docker образа в качестве среды выполнения
- Файловые операции: Простая передача файлов и директорий между хостом и контейнерами
- Выполнение команд: Запуск любых shell команд внутри контейнеризованной среды
- Логирование в реальном времени: Трансляция логов контейнера и вывода команд в реальном времени
- Автообновления: Встроенная проверка обновлений и автоматическое обновление бинарных файлов
- Мультиплатформенность: Поддерживает Linux, macOS и Windows
- Ресурс логов контейнера: Динамический ресурс, предоставляющий доступ к логам контейнера
- Изолированная среда выполнения с использованием Docker контейнеров
- Ограничения ресурсов через ограничения Docker контейнера

## Ресурсы

- [GitHub Repository](https://github.com/Automata-Labs-team/code-sandbox-mcp)

## Примечания

Требует установленный и запущенный Docker. Установщик автоматически проверяет установку Docker и создает необходимые файлы конфигурации. Логи контейнера доступны как динамический ресурс по адресу 'containers://{id}/logs' с MIME типом 'text/plain'.