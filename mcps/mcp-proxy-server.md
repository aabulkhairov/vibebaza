---
title: MCP Proxy Server MCP сервер
description: Прокси MCP сервер, который агрегирует несколько MCP серверов за единой HTTP точкой входа, позволяя объединить инструменты, промпты и ресурсы от многих серверов в один унифицированный интерфейс.
tags:
- Integration
- API
- DevOps
- Productivity
author: TBXark
featured: true
---

Прокси MCP сервер, который агрегирует несколько MCP серверов за единой HTTP точкой входа, позволяя объединить инструменты, промпты и ресурсы от многих серверов в один унифицированный интерфейс.

## Установка

### Из исходного кода

```bash
git clone https://github.com/TBXark/mcp-proxy.git
cd mcp-proxy
make build
./build/mcp-proxy --config path/to/config.json
```

### Go Install

```bash
go install github.com/TBXark/mcp-proxy@latest
```

### Docker

```bash
docker run -d -p 9090:9090 -v /path/to/config.json:/config/config.json ghcr.io/tbxark/mcp-proxy:latest
```

### Docker с удалённой конфигурацией

```bash
docker run -d -p 9090:9090 ghcr.io/tbxark/mcp-proxy:latest --config https://example.com/config.json
```

## Возможности

- Проксирование нескольких MCP клиентов: агрегирует инструменты, промпты и ресурсы от многих серверов
- SSE и потоковый HTTP: обслуживание через Server‑Sent Events или потоковый HTTP
- Гибкая конфигурация: поддерживает типы клиентов stdio, sse и streamable-http
- Поддержка Docker с npx и uvx для запуска MCP серверов

## Ресурсы

- [GitHub Repository](https://github.com/TBXark/mcp-proxy)

## Примечания

Документация по конфигурации, примеры использования и руководства по развертыванию доступны в отдельных файлах документации. Онлайн конвертер конфигурации Claude доступен по адресу https://tbxark.github.io/mcp-proxy. Проект вдохновлен adamwattis/mcp-proxy-server и включает MIT лицензию.