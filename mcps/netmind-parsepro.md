---
title: NetMind ParsePro MCP сервер
description: Высококачественный, надежный и экономичный AI-сервис для парсинга PDF, который преобразует PDF-файлы в указанные форматы вывода, такие как JSON и Markdown, с поддержкой как локальных файлов, так и удаленных URL.
tags:
- AI
- Media
- API
- Productivity
- Integration
author: protagolabs
featured: false
---

Высококачественный, надежный и экономичный AI-сервис для парсинга PDF, который преобразует PDF-файлы в указанные форматы вывода, такие как JSON и Markdown, с поддержкой как локальных файлов, так и удаленных URL.

## Установка

### UV (Homebrew)

```bash
brew install uv
```

### UV (curl)

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### UV (Windows PowerShell)

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### UVX

```bash
uvx netmind-parse-pdf-mcp
```

## Конфигурация

### Cursor & Claude Desktop & Windsurf

```json
{
  "mcpServers": {
    "parse-pdf": {
      "env": {
        "NETMIND_API_TOKEN": "XXXXXXXXXXXXXXXXXXXX"
      },
      "command": "uvx",
      "args": [
        "netmind-parse-pdf-mcp"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `parse_pdf` | Парсит PDF-файл и возвращает извлеченный контент в указанном формате (JSON или Markdown)... |

## Возможности

- Конвертация PDF-файлов в форматы JSON или Markdown
- Поддержка как локальных путей к файлам, так и удаленных URL
- Высококачественный, надежный и экономичный парсинг
- Готовность к работе с MCP сервером для бесшовной интеграции с AI-агентами
- Структурированный вывод JSON или форматирование в виде Markdown строки

## Переменные окружения

### Обязательные
- `NETMIND_API_TOKEN` - Ваш API-ключ Netmind, полученный с https://www.netmind.ai/user/apiToken

## Ресурсы

- [GitHub Repository](https://github.com/protagolabs/Netmind-Parse-PDF-MCP)

## Примечания

Расположение конфигурационных файлов различается в зависимости от платформы: Cursor использует ~/.cursor/mcp.json (macOS) или C:\Users\your-username\.cursor\mcp.json (Windows), Claude использует ~/Library/Application Support/Claude/claude_desktop_config.json (macOS) или %APPDATA%/Claude/claude_desktop_config.json (Windows), Windsurf использует ~/.codeium/windsurf/mcp_config.json (macOS) или C:\Users\your-username\.codeium\windsurf\mcp_config.json (Windows). Попробуйте playground на https://www.netmind.ai/AIServices/parse-pdf