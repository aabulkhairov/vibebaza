---
title: Netbird MCP сервер
description: MCP сервер, который предоставляет доступ только для чтения к конфигурации и статусу сети Netbird, позволяя LLM анализировать сетевые пиры, группы, политики, проверки состояния, сети, серверы имен и распределение портов.
tags:
- DevOps
- Security
- Monitoring
- API
- Cloud
author: aantti
featured: false
---

MCP сервер, который предоставляет доступ только для чтения к конфигурации и статусу сети Netbird, позволяя LLM анализировать сетевые пиры, группы, политики, проверки состояния, сети, серверы имен и распределение портов.

## Установка

### Из исходников

```bash
git clone https://github.com/aantti/mcp-netbird
cd mcp-netbird && make install
```

### Go Install

```bash
go install github.com/aantti/mcp-netbird/cmd/mcp-netbird@latest
```

### Smithery

```bash
npx -y @smithery/cli install @aantti/mcp-netbird --client claude
```

### Docker

```bash
docker build -t mcp-netbird-sse:v1 -f Dockerfile.sse .
docker run --name mcp-netbird -p 8001:8001 -e NETBIRD_API_TOKEN=<your-api-token> mcp-netbird-sse:v1
```

## Конфигурация

### Codeium Windsurf

```json
{
  "mcpServers": {
    "netbird": {
      "command": "mcp-netbird",
      "args": [],
      "env": {
        "NETBIRD_API_TOKEN": "<your-api-token>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_netbird_peers` | Список всех сетевых пиров |
| `list_netbird_port_allocations` | Список всех входящих портов для конкретного ID пира |
| `list_netbird_groups` | Список всех групп |
| `list_netbird_policies` | Список всех политик |
| `list_netbird_posture_checks` | Список всех проверок состояния |
| `list_netbird_networks` | Список всех сетей |
| `list_netbird_nameservers` | Список всех групп серверов имен |

## Возможности

- Использует Netbird API для доступа к конфигурации и статусу
- Настраиваемая конечная точка API
- Безопасная аутентификация на основе токенов для Netbird API
- Соответствие 1:1 выбранных ресурсов Netbird API только для чтения с инструментами

## Переменные окружения

### Обязательные
- `NETBIRD_API_TOKEN` - Ваш токен Netbird API

### Опциональные
- `NETBIRD_HOST` - Хост Netbird API (по умолчанию api.netbird.io)

## Примеры использования

```
Can you explain my Netbird peers, groups and policies to me?
```

## Ресурсы

- [GitHub Repository](https://github.com/aantti/mcp-netbird)

## Примечания

Проект все еще в разработке. Основан на MCP сервере для Grafana от Grafana Labs и использует MCP Go от Mark III Labs. Требует токен Netbird API из консоли управления. Может быть запущен через Docker, ToolHive или вручную для разработки.