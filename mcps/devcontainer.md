---
title: Devcontainer MCP сервер
description: MCP сервер для devcontainer, который позволяет генерировать и настраивать контейнеры разработки напрямую из конфигурационных файлов devcontainer.json, используя devcontainers CLI.
tags:
- DevOps
- Code
- Productivity
author: AI-QL
featured: false
---

MCP сервер для devcontainer, который позволяет генерировать и настраивать контейнеры разработки напрямую из конфигурационных файлов devcontainer.json, используя devcontainers CLI.

## Установка

### NPX

```bash
npx -y mcp-devcontainers
```

### NPM Install

```bash
npm install
```

### STDIO Transport

```bash
npm start
```

### SSE Transport

```bash
npm start sse
```

### HTTP Transport

```bash
npm start http
```

## Конфигурация

### MCP Remote Client

```json
{
  "mcpServers": {
    "Devcontainer": {
      "command": "npx",
      "args": ["mcp-remote", "https://ominous-halibut-7vvq7v56vgq6hr5p9-3001.app.github.dev/mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `devcontainer_up` | Инициализирует и запускает devcontainer окружение в указанной рабочей папке |
| `devcontainer_run_user_commands` | Выполняет пользовательские скрипты postCreateCommand и postStartCommand внутри devcontainer |
| `devcontainer_exec` | Запускает пользовательскую команду shell внутри devcontainer для указанного рабочего пространства |
| `devcontainer_cleanup` | Выполняет команду docker для очистки всех devcontainer окружений |
| `devcontainer_list` | Выполняет команду docker для получения списка всех devcontainer окружений |
| `devcontainer_workspace_folders` | Выполняет команду find для получения всех рабочих папок с конфигурацией devcontainer |

## Возможности

- Инициализация и запуск devcontainer окружений
- Выполнение команд после создания и после запуска
- Запуск произвольных команд внутри devcontainer
- Список и очистка devcontainer окружений
- Поиск рабочих папок с конфигурациями devcontainer
- Множественные варианты транспорта (STDIO, SSE, HTTP)
- Построен на базе devcontainers/cli

## Ресурсы

- [GitHub Repository](https://github.com/AI-QL/mcp-devcontainers)

## Примечания

Docker требуется в окружении выполнения. Для пробной версии GitHub Codespaces сделайте переадресованный порт публично доступным и добавьте '/mcp' к URL для потоковых HTTP соединений. Команда devcontainer_up обычно требует значительного времени для запуска контейнеров.