---
title: nomad-mcp сервер
description: MCP сервер на Golang, который предоставляет инструменты для подключения к кластерам HashiCorp Nomad и управления ими через Model Context Protocol.
tags:
- DevOps
- Cloud
- Monitoring
- API
author: kocierik
featured: false
install_command: npx -y @smithery/cli install @kocierik/mcp-nomad --client claude
---

MCP сервер на Golang, который предоставляет инструменты для подключения к кластерам HashiCorp Nomad и управления ими через Model Context Protocol.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @kocierik/mcp-nomad --client claude
```

### mcp-get

```bash
npx @michaellatman/mcp-get@latest install @kocierik/mcp-nomad
```

### NPM Global

```bash
npm install -g @kocierik/mcp-nomad
```

### Go Install

```bash
go get github.com/kocierik/mcp-nomad
go install github.com/kocierik/mcp-nomad
```

### Docker Linux

```bash
docker run -i --rm --network=host kocierik/mcpnomad-server:latest
```

## Конфигурация

### Claude Desktop Basic

```json
{
  "mcpServers": {
    "mcp_nomad": {
      "command": "mcp-nomad",
      "args": [],
      "env": {
        "NOMAD_TOKEN": "${NOMAD_TOKEN}",
        "NOMAD_ADDR": "${NOMAD_ADDR}"
      }
    }
  }
}
```

### Claude Docker macOS/Windows

```json
{
  "mcpServers": {
    "mcp_nomad": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e", "NOMAD_TOKEN=secret-token-acl-optional", 
        "-e", "NOMAD_ADDR=http://host.docker.internal:4646",
        "mcpnomad/server:latest"
      ]
    }
  }
}
```

### Claude Docker Linux

```json
{
  "mcpServers": {
    "mcp_nomad": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "NOMAD_ADDR=http://172.17.0.1:4646",
        "-e", "NOMAD_TOKEN=secret-token-acl-optional", 
        "kocierik/mcpnomad-server:latest"
      ]
    }
  }
}
```

## Возможности

- Подключение к кластерам HashiCorp Nomad
- Множественные типы транспорта (stdio, sse, streamable-http)
- Настраиваемый адрес и порт сервера Nomad
- Поддержка токенов Nomad ACL
- Доступен в виде готовых бинарных файлов и Docker образов

## Переменные окружения

### Опциональные
- `NOMAD_ADDR` - адрес Nomad HTTP API
- `NOMAD_TOKEN` - токен Nomad ACL

## Ресурсы

- [GitHub Repository](https://github.com/kocierik/mcp-nomad)

## Примечания

Сервер поддерживает множество способов установки и вариантов деплоя, включая Docker контейнеры. Опции командной строки включают -nomad-addr (по умолчанию http://localhost:4646), -port (по умолчанию 8080) и -transport (по умолчанию stdio). Лицензирован под MIT License.