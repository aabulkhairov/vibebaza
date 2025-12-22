---
title: MasterGo MCP сервер
description: Автономный MCP сервис, который связывает инструменты дизайна MasterGo с AI моделями, обеспечивая прямое получение DSL данных из файлов дизайна MasterGo.
tags:
- API
- Integration
- Productivity
- Code
author: mastergo-design
featured: true
install_command: npx -y @smithery/cli install @mastergo-design/mastergo-magic-mcp
  --client claude
---

Автономный MCP сервис, который связывает инструменты дизайна MasterGo с AI моделями, обеспечивая прямое получение DSL данных из файлов дизайна MasterGo.

## Установка

### NPX

```bash
npx @mastergo/magic-mcp --token=YOUR_TOKEN [--url=API_URL] [--rule=RULE_NAME] [--debug] [--no-rule]
```

### Smithery

```bash
npx -y @smithery/cli install @mastergo-design/mastergo-magic-mcp --client claude
```

### Из исходного кода

```bash
yarn
yarn build
```

## Конфигурация

### Cursor (аргументы командной строки)

```json
{
  "mcpServers": {
    "mastergo-magic-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "@mastergo/magic-mcp",
        "--token=<MG_MCP_TOKEN>",
        "--url=https://mastergo.com"
      ],
      "env": {}
    }
  }
}
```

### Cursor (переменные окружения)

```json
{
  "mcpServers": {
    "mastergo-magic-mcp": {
      "command": "npx",
      "args": ["-y", "@mastergo/magic-mcp"],
      "env": {
        "MG_MCP_TOKEN": "<YOUR_TOKEN>",
        "API_BASE_URL": "https://mastergo.com"
      }
    }
  }
}
```

### Cline (аргументы командной строки)

```json
{
  "mcpServers": {
    "@master/mastergo-magic-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "@mastergo/magic-mcp",
        "--token=<MG_MCP_TOKEN>",
        "--url=https://mastergo.com"
      ],
      "env": {}
    }
  }
}
```

### Cline (переменные окружения)

```json
{
  "mcpServers": {
    "@master/mastergo-magic-mcp": {
      "command": "npx",
      "args": ["-y", "@mastergo/magic-mcp"],
      "env": {
        "MG_MCP_TOKEN": "<YOUR_TOKEN>",
        "API_BASE_URL": "https://mastergo.com"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-dsl` | Инструмент для получения DSL (Domain Specific Language) данных из файлов дизайна MasterGo |
| `get-component-link` | Инструмент для получения документации компонентов по ссылкам |
| `get-meta` | Инструмент для получения метаданных |
| `get-component-workflow` | Инструмент, предоставляющий структурированный рабочий процесс разработки компонентов для Vue и React, генерирующий... |

## Возможности

- Получает DSL данные из файлов дизайна MasterGo
- Запускается напрямую через npx
- Не требует внешних зависимостей, нужна только среда Node.js
- Поддерживает конфигурацию правил дизайна
- Режим отладки для подробной информации об ошибках

## Переменные окружения

### Обязательные
- `MG_MCP_TOKEN` - токен MasterGo API для аутентификации
- `MASTERGO_API_TOKEN` - альтернативная переменная окружения для токена MasterGo API

### Опциональные
- `API_BASE_URL` - базовый URL API для сервиса MasterGo
- `RULES` - JSON массив правил (например, '["rule1", "rule2"]')

## Ресурсы

- [GitHub Repository](https://github.com/mastergo-design/mastergo-magic-mcp)

## Примечания

Токен можно получить в личных настройках MasterGo на вкладке Security Settings. Сервер поддерживает как аргументы командной строки, так и переменные окружения для конфигурации. Доступен в маркетплейсе расширений LINGMA VSCode для простой интеграции.