---
title: FDIC BankFind MCP сервер - (Unofficial) MCP
description: MCP сервер, который предоставляет доступ к FDIC BankFind API для запросов
  структурированных банковских данных США, включая демографию банков, банкротства, местоположения филиалов
  и регуляторную информацию.
tags:
- API
- Finance
- Database
- Analytics
author: Community
featured: false
---

MCP сервер, который предоставляет доступ к FDIC BankFind API для запросов структурированных банковских данных США, включая демографию банков, банкротства, местоположения филиалов и регуляторную информацию.

## Установка

### Docker (рекомендуется)

```bash
docker run -i --rm ghcr.io/clafollett/fdic-bank-find-mcp-server:main
```

### Ручная сборка Docker

```bash
git clone https://github.com/YOUR-ORG/fdic-bank-find-mcp-server.git
cd fdic-bank-find-mcp-server
docker build -t fdic-bank-find-mcp-server:main .
docker run -i --rm fdic-bank-find-mcp-server:main
```

### Из исходников

```bash
git clone https://github.com/YOUR-ORG/fdic-bank-find-mcp-server.git
cd fdic-bank-find-mcp-server
cargo build --release
```

### MCP Inspector

```bash
npx @modelcontextprotocol/inspector docker run -i --rm fdic-bank-find-mcp-server:main
```

## Конфигурация

### VS Code

```json
{
  "mcp": {
    "servers": {
      "fdic": {
        "command": "docker",
        "args": [
          "run",
          "-i",
          "--rm",
          "ghcr.io/YOUR-ORG/fdic-bank-find-mcp-server:main"
        ]
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "fdic-bank-find": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "ghcr.io/YOUR-ORG/fdic-bank-find-mcp-server:main"
      ]
    }
  }
}
```

### VS Code (из исходников)

```json
{
  "mcp": {
    "servers": {
      "fdic": {
        "command": "/path/to/repository/fdic-bank-find-mcp-server/target/release/fdic-bank-find-mcp-server"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_demographics` | Демографические сводки |
| `get_failures` | Исторические банкротства банков |
| `get_history` | События изменения структуры |
| `get_institutions` | Демография учреждений |
| `get_locations` | Местоположения филиалов |
| `get_sod` | Сводка депозитов |
| `get_summary` | Исторические агрегаты по годам |

## Возможности

- Доступ к FDIC BankFind API для структурированных банковских данных США
- Поддержка фильтрации, пагинации, сортировки и выбора полей
- Множественные форматы вывода (JSON, CSV, XML)
- Возможности загрузки файлов
- Функциональность агрегации и поиска
- Все эндпоинты FDIC Bank Find API кроме /financials
- Развертывание на базе Docker для легкой интеграции

## Примеры использования

```
Исследования агентов/LLM по банкам и учреждениям США
```

```
Автоматизация финансовой аналитики, соответствия требованиям и рабочих процессов отчетности
```

```
Создание дашбордов, ботов или кастомных fintech инструментов на базе ИИ
```

```
Быстрое прототипирование для академических или рыночных исследований
```

## Ресурсы

- [GitHub Repository](https://github.com/clafollett/fdic-bank-find-mcp-server)

## Примечания

Эндпоинт /financials не реализован из-за сложности схемы, которая превышает лимиты компилятора Rust. Все инструменты принимают общие параметры как api_key, filters, fields, limit, offset, sort_by, sort_order, file_format, file_download и file_name. Проект был создан в стиле 'vibe coding' с помощью ИИ и подчеркивает креативную, коллаборативную разработку.