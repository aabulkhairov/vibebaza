---
title: sslmon MCP сервер
description: MCP сервер, который предоставляет информацию о регистрации доменов
  и возможности мониторинга SSL сертификатов для контроля безопасности, управления доменами
  и отслеживания жизненного цикла сертификатов.
tags:
- Security
- Monitoring
- API
author: Community
featured: false
install_command: claude mcp add sslmon -- npx -y sslmon-mcp
---

MCP сервер, который предоставляет информацию о регистрации доменов и возможности мониторинга SSL сертификатов для контроля безопасности, управления доменами и отслеживания жизненного цикла сертификатов.

## Установка

### Удаленный HTTP сервер

```bash
claude mcp add -t http sslmon https://sslmon.dev/mcp
```

### NPX Mac/Linux

```bash
claude mcp add sslmon -- npx -y sslmon-mcp
```

### NPX Windows

```bash
claude mcp add sslmon -- cmd /c npx -y sslmon-mcp
```

## Конфигурация

### Claude Desktop JSON

```json
{
  "mcpServers": {
    "sslmon": {
      "command": "npx",
      "args": ["-y", "sslmon-mcp"],
      "env": {}
    }
  }
}
```

### TOML конфигурация

```json
[mcp_servers.sslmon]
command = "npx"
args = ["-y", "sslmon-mcp"]
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_domain_info` | Получить информацию о регистрации домена и сроке истечения, включая дату регистрации, дату истечения, ... |
| `get_ssl_cert_info` | Получить информацию об SSL сертификате и статусе валидности, включая действительные даты, издателя, субъекта, валид... |

## Возможности

- Информация о регистрации домена - получайте даты регистрации и истечения домена
- Информация об SSL сертификате - проверяйте периоды действия SSL сертификатов и их детали

## Ресурсы

- [GitHub Repository](https://github.com/firesh/sslmon-mcp)

## Примечания

Доступен как удаленный HTTP сервер (https://sslmon.dev/mcp), так и для локальной установки через NPX. Поддерживает несколько языков (английский, китайский, японский). Включает интеграцию с glama.ai бейджем.