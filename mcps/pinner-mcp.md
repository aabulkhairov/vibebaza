---
title: Pinner MCP сервер
description: MCP сервер, который помогает закреплять сторонние зависимости, такие как Docker базовые образы и GitHub Actions, к неизменяемым дайджестам/хэшам коммитов для безопасности цепочки поставок.
tags:
- Security
- DevOps
- Code
author: Community
featured: false
---

MCP сервер, который помогает закреплять сторонние зависимости, такие как Docker базовые образы и GitHub Actions, к неизменяемым дайджестам/хэшам коммитов для безопасности цепочки поставок.

## Установка

### Docker

```bash
docker run -it --rm ghcr.io/safedep/pinner-mcp:latest
```

### Локальная сборка

```bash
docker build -t pinner-mcp:local .
```

## Конфигурация

### VS Code

```json
{
  "servers": {
    "pinner-mcp": {
      "type": "stdio",
      "command": "docker",
      "args": ["run", "--rm", "-i", "ghcr.io/safedep/pinner-mcp:latest"]
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "pinner-mcp-stdio-server": {
      "command": "docker",
      "args": ["run", "--rm", "-i", "ghcr.io/safedep/pinner-mcp:latest"]
    }
  }
}
```

## Возможности

- Закрепление Docker базовых образов к неизменяемым дайджестам
- Закрепление GitHub Actions к хэшам коммитов
- Обновление закрепленных версий зависимостей
- Предотвращение атак на цепочку поставок

## Примеры использования

```
Pin GitHub Actions to their commit hash
```

```
Pin container base images to digests
```

```
Update pinned versions of container base images
```

## Ресурсы

- [GitHub Repository](https://github.com/safedep/pinner-mcp)

## Примечания

Обновления автоматически отправляются в тег 'latest' в GitHub Container Registry. Вам необходимо вручную загружать обновления с помощью 'docker pull ghcr.io/safedep/pinner-mcp:latest'. Изначально был создан для защиты проекта 'vet' от вредоносных GitHub Actions.