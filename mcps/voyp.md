---
title: Voyp MCP сервер
description: MCP сервер, который позволяет AI-ассистентам совершать телефонные звонки через сервис VOYP, обеспечивая возможности записи на приём, резервирования, консультаций и мониторинга звонков.
tags:
- AI
- API
- Integration
- Productivity
- Messaging
author: Community
featured: false
install_command: npx -y @smithery/cli install @paulotaylor/voyp-mcp --client claude
---

MCP сервер, который позволяет AI-ассистентам совершать телефонные звонки через сервис VOYP, обеспечивая возможности записи на приём, резервирования, консультаций и мониторинга звонков.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @paulotaylor/voyp-mcp --client claude
```

### NPX

```bash
npx -y voyp-mcp@0.1.0
```

### Из исходного кода

```bash
git clone https://github.com/paulotaylor/voyp-mcp.git
cd voyp-mcp
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "voyp-mcp": {
      "command": "npx",
      "args": ["-y", "voyp-mcp"],
      "env": {
        "VOYP_API_KEY": "your-VOYP-api-key"
      }
    }
  }
}
```

### Claude Desktop (Git)

```json
{
  "mcpServers": {
    "voyp": {
      "command": "npx",
      "args": ["/path/to/voyp-mcp/build/index.js"],
      "env": {
        "VOYP_API_KEY": "your-VOYP-api-key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `start_call` | Начать телефонные звонки с созданным контекстом вызова |
| `hangup_call` | Завершить активные телефонные звонки |

## Возможности

- Создание надёжных контекстов звонков для использования при совершении вызовов
- Поиск информации о бизнесе при звонках в рестораны, стоматологии и т.д.
- Звонки и запись на приём, резервирование, консультации, запросы
- Предоставление статуса звонка
- Завершение звонка
- Поддержка OAuth2 потока аутентификации
- Доступна удалённая HTTP конечная точка с поддержкой потоковой передачи

## Переменные окружения

### Обязательные
- `VOYP_API_KEY` - Ваш API ключ VOYP для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/paulotaylor/voyp-mcp)

## Примечания

Требует API ключ VOYP и кредиты для совершения звонков. Поддерживает удалённую HTTP конечную точку с потоковой передачей на https://api.voyp.app/mcp/stream. Совместим с Claude Desktop, Goose и другими MCP клиентами. Требует Node.js версии 20 или выше.