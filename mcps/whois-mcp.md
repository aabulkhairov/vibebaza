---
title: Whois MCP сервер
description: MCP сервер, который позволяет AI агентам выполнять WHOIS запросы для доменов, IP адресов, ASN и TLD, чтобы получить информацию о регистрации, владельцах и другие связанные с доменами данные.
tags:
- Security
- API
- DevOps
- Monitoring
- Productivity
author: Community
featured: false
---

MCP сервер, который позволяет AI агентам выполнять WHOIS запросы для доменов, IP адресов, ASN и TLD, чтобы получить информацию о регистрации, владельцах и другие связанные с доменами данные.

## Установка

### NPX Global

```bash
npx -y @bharathvaj/whois-mcp@latest
```

### Из исходного кода

```bash
# Установка зависимостей
pnpm install

# Сборка
pnpm build
```

## Конфигурация

### Cursor IDE Global

```json
Name: Whois Lookup
Type: command
Command: npx -y @bharathvaj/whois-mcp@latest
```

### Cursor Project

```json
{
  "mcpServers": {
    "whois": {
      "command": "npx",
      "args": [
        "-y",
        "@bharathvaj/whois-mcp@latest"
      ]
    }
  }
}
```

### Roo Code

```json
{
  "mcpServers": {
    "whois": {
      "command": "npx",
      "args": [
        "-y",
        "@bharathvaj/whois-mcp@latest"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `whois_domain` | Поиск whois информации о домене |
| `whois_tld` | Поиск whois информации о домене верхнего уровня (TLD) |
| `whois_ip` | Поиск whois информации об IP адресе |
| `whois_as` | Поиск whois информации о номере автономной системы (ASN) |

## Возможности

- Проверка доступности домена напрямую через AI агентов
- Получение информации о владельцах домена
- Получение дат регистрации и истечения срока действия
- Поиск информации о регистраторе
- Поиск серверов имен и DNS деталей
- Проверка статуса домена (активный, истекший, заблокированный)
- Получение контактной информации для доменов (если не защищена приватностью)
- Выполнение WHOIS запросов для IP адресов
- Запрос информации о номере автономной системы (ASN)
- Поиск деталей домена верхнего уровня (TLD)

## Примеры использования

```
Check if a domain is available
```

```
Who owns this domain?
```

```
When was this domain registered?
```

```
When does this domain expire?
```

```
What are the name servers for this domain?
```

## Ресурсы

- [GitHub Repository](https://github.com/bharathvaj-ganesan/whois-mcp)

## Примечания

Совместим с Claude Desktop, Cursor, Windsurf и другими AI агентами. Включает поддержку отладки через MCP Inspector. Может использоваться как для глобальной, так и для проектной установки.