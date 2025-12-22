---
title: FoundationModels MCP сервер
description: MCP сервер, который предоставляет возможности генерации текста с использованием фреймворка Foundation Models от Apple, обеспечивая безопасный и приватный доступ к языковым моделям на устройстве для MCP клиентов.
tags:
- AI
- Security
- Integration
author: phimage
featured: false
---

MCP сервер, который предоставляет возможности генерации текста с использованием фреймворка Foundation Models от Apple, обеспечивая безопасный и приватный доступ к языковым моделям на устройстве для MCP клиентов.

## Установка

### Из исходного кода

```bash
git clone <repository-url>
cd mcp-foundation-models
swift build -c release
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "foundation-models": {
      "command": "/path/to/mcp-foundation-models/.build/release/mcp-foundation-models",
      "args": [
      ]
    }
  }
}
```

## Возможности

- Интеграция с Apple Foundation Models: Использует языковые модели Apple на устройстве для генерации текста
- Безопасная и приватная генерация текста с использованием моделей на устройстве
- Требует macOS 26.0+ и Apple Silicon для оптимальной производительности

## Переменные окружения

### Опциональные
- `SYSTEM_INSTRUCTIONS` - Установить системные инструкции по умолчанию для AI ассистента
- `DEBUG` - Включить отладочное логирование (любое непустое значение)

## Ресурсы

- [GitHub Repository](https://github.com/phimage/mcp-foundation-models)

## Примечания

Требует macOS 26.0 или выше (macOS Tahoe), Xcode 26.0+, Swift 6.2+ и Mac с Apple Silicon для оптимальной производительности Foundation Models. Создан с зависимостями Swift, включая swift-argument-parser, MCP Swift SDK и swift-service-lifecycle. В планах добавление управления сессиями для истории разговоров.