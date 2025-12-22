---
title: ggRMCP MCP сервер
description: Высокопроизводительный шлюз на основе Go, который преобразует gRPC сервисы в MCP-совместимые инструменты, позволяя AI моделям вроде Claude напрямую вызывать ваши gRPC сервисы без модификаций.
tags:
- API
- Integration
- DevOps
- AI
author: aalobaidi
featured: false
---

Высокопроизводительный шлюз на основе Go, который преобразует gRPC сервисы в MCP-совместимые инструменты, позволяя AI моделям вроде Claude напрямую вызывать ваши gRPC сервисы без модификаций.

## Установка

### Из исходного кода

```bash
git clone https://github.com/aalobaidi/ggRMCP
cd ggRMCP
go mod download
go build -o build/grmcp ./cmd/grmcp
```

### MCP Remote Client

```bash
npm install -g mcp-remote
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "grpc-gateway": {
      "command": "mcp-remote",
      "args": ["http://localhost:50053"],
      "env": {}
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `Dynamic gRPC Methods` | Каждый gRPC метод становится MCP инструментом с автоматической генерацией схемы и валидацией |

## Возможности

- Языково-независимый - работает как sidecar с gRPC сервисами на любом языке
- Бесшовная интеграция с существующими gRPC сервисами без модификаций
- Динамическое обнаружение сервисов с использованием gRPC server reflection или FileDescriptorSet
- Генерация инструментов в реальном времени с извлечением комментариев из protobuf определений
- Автоматическая валидация запросов/ответов с использованием protobuf схем
- Управление состоянием сессий для сложных AI взаимодействий
- Настраиваемая передача HTTP заголовков с фильтрацией безопасности
- Поддержка FileDescriptorSet для богатых схем инструментов с документацией
- Паттерны развертывания sidecar или централизованного шлюза

## Примеры использования

```
Ask Claude to list available gRPC service tools
```

```
Call specific gRPC methods through Claude
```

```
Handle complex request/response data with automatic validation
```

## Ресурсы

- [GitHub Repository](https://github.com/aalobaidi/ggRMCP)

## Примечания

ggRMCP является экспериментальным и не готов для продакшена. Поддерживает как sidecar развертывание рядом с gRPC сервисами, так и паттерны централизованного шлюза. Шлюз может использовать gRPC reflection для динамического обнаружения или файлы FileDescriptorSet для улучшенных схем с комментариями. Порты по умолчанию: 50051 для gRPC и 50053 для HTTP/MCP.