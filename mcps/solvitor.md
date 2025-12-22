---
title: Solvitor MCP сервер
description: Model Context Protocol (MCP) сервер для взаимодействия с Solvitor API, предоставляющий инструменты для извлечения IDL файлов из закрытых Solana смарт-контрактов с использованием техник реверс-инжиниринга.
tags:
- API
- Code
- Security
- Analytics
- Integration
author: Community
featured: false
---

Model Context Protocol (MCP) сервер для взаимодействия с Solvitor API, предоставляющий инструменты для извлечения IDL файлов из закрытых Solana смарт-контрактов с использованием техник реверс-инжиниринга.

## Установка

### Cargo Install

```bash
cargo install solvitor-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "solvitor-mcp": {
      "command": "/Users/$username/.cargo/bin/solvitor-mcp",
      "args": [],
      "env": {
        "SOLVITOR_API_KEY": "your_solvitor_api_key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `decode` | Извлекает IDL (Interface Definition Language) из любой Solana программы с использованием техник реверс-инжиниринга... |

## Возможности

- Извлечение IDL файлов из закрытых Solana смарт-контрактов
- Декомпиляция Solana программ с использованием AI-powered реверс-инжиниринга
- Поддержка как Anchor, так и нативных Solana программ
- Настраиваемая Solana RPC endpoint
- Возвращает структурированный IDL с метаданными программы и информацией о типах

## Переменные окружения

### Обязательные
- `SOLVITOR_API_KEY` - API ключ для доступа к сервису Solvitor

## Ресурсы

- [GitHub Repository](https://github.com/Adeptus-Innovatio/solvitor-mcp)

## Примечания

Требует Rust toolchain для установки. Solvitor API ключ можно получить бесплатно на https://solvitor.xyz/developer-settings. Remote MCP функциональность доступна по запросу.