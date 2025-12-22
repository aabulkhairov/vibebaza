---
title: Pacman MCP сервер
description: MCP сервер, который предоставляет возможности для запросов к индексам пакетов, позволяя LLM искать и получать информацию из репозиториев пакетов, таких как PyPI, npm, crates.io, Docker Hub и Terraform Registry.
tags:
- Search
- DevOps
- Code
- API
- Integration
author: oborchers
featured: false
---

MCP сервер, который предоставляет возможности для запросов к индексам пакетов, позволяя LLM искать и получать информацию из репозиториев пакетов, таких как PyPI, npm, crates.io, Docker Hub и Terraform Registry.

## Установка

### uv (рекомендуется)

```bash
uvx mcp-server-pacman
```

### PIP

```bash
pip install mcp-server-pacman
python -m mcp_server_pacman
```

### Docker

```bash
docker pull oborchers/mcp-server-pacman:latest
docker run -i --rm oborchers/mcp-server-pacman
```

## Конфигурация

### Claude Desktop (uvx)

```json
"mcpServers": {
  "pacman": {
    "command": "uvx",
    "args": ["mcp-server-pacman"]
  }
}
```

### Claude Desktop (docker)

```json
"mcpServers": {
  "pacman": {
    "command": "docker",
    "args": ["run", "-i", "--rm", "oborchers/mcp-server-pacman:latest"]
  }
}
```

### Claude Desktop (pip)

```json
"mcpServers": {
  "pacman": {
    "command": "python",
    "args": ["-m", "mcp-server-pacman"]
  }
}
```

### VS Code (uvx)

```json
{
  "mcp": {
    "servers": {
      "pacman": {
        "command": "uvx",
        "args": ["mcp-server-pacman"]
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_package` | Поиск пакетов в индексах пакетов (PyPI, npm, crates.io, Terraform) |
| `package_info` | Получение подробной информации о конкретном пакете |
| `search_docker_image` | Поиск Docker образов в Docker Hub |
| `docker_image_info` | Получение подробной информации о конкретном Docker образе |
| `terraform_module_latest_version` | Получение последней версии Terraform модуля |

## Возможности

- Поиск и получение информации из PyPI, npm, crates.io, Docker Hub и Terraform Registry
- Получение подробной информации о пакетах, включая версии и метаданные
- Поиск Docker образов и получение информации об образах
- Запросы к Terraform модулям и получение информации о версиях
- Настраиваемый user-agent для API запросов
- Встроенная функциональность кэширования
- Настраиваемые лимиты результатов (до 50 результатов)

## Примеры использования

```
Search for Python packages on PyPI
```

```
Get information about a specific Python package
```

```
Search for JavaScript packages on npm
```

```
Get information about a specific JavaScript package
```

```
Search for Rust packages on crates.io
```

## Ресурсы

- [GitHub Repository](https://github.com/oborchers/mcp-server-pacman)

## Примечания

Сервер использует стандартный user-agent 'ModelContextProtocol/1.0 Pacman (+https://github.com/modelcontextprotocol/servers)', который можно настроить, добавив '--user-agent=YourUserAgent' в список аргументов. Проект включает комплексное тестирование, поддержку отладки с помощью MCP inspector и автоматизированный процесс релизов через GitHub Actions.