---
title: Simple Loki MCP сервер
description: MCP сервер, который предоставляет AI ассистентам доступ к запросам и анализу логов из Grafana Loki с использованием LogQL, с автоматическим переключением на HTTP API когда logcli недоступен.
tags:
- Monitoring
- DevOps
- Analytics
- API
author: ghrud92
featured: false
---

MCP сервер, который предоставляет AI ассистентам доступ к запросам и анализу логов из Grafana Loki с использованием LogQL, с автоматическим переключением на HTTP API когда logcli недоступен.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @ghrud92/simple-loki-mcp --client claude
```

### NPX

```bash
npx -y simple-loki-mcp
```

### Из исходного кода

```bash
git clone https://github.com/ghrud92/loki-mcp.git
cd loki-mcp
npm install
npm run build
```

## Конфигурация

### MCP конфигурация

```json
{
  "mcpServers": {
    "simple-loki": {
      "command": "npx",
      "args": ["-y", "simple-loki-mcp"],
      "env": {
        "LOKI_ADDR": "https://loki.sup.band"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `query-loki` | Запрос логов из Loki с опциями фильтрации используя синтаксис LogQL |
| `get-label-values` | Получение всех значений для конкретного лейбла |
| `get-labels` | Получение всех доступных лейблов |

## Возможности

- Запрос логов Loki с полной поддержкой LogQL
- Получение значений лейблов и метаданных
- Поддержка аутентификации и конфигурации через переменные окружения или конфигурационные файлы
- Предоставляет отформатированные результаты в различных выходных форматах (по умолчанию, raw, JSON lines)
- Автоматическое переключение на HTTP API когда logcli недоступен в окружении

## Переменные окружения

### Обязательные
- `LOKI_ADDR` - Адрес сервера Loki (URL)

### Опциональные
- `LOKI_USERNAME` - Имя пользователя для базовой аутентификации
- `LOKI_PASSWORD` - Пароль для базовой аутентификации
- `LOKI_TENANT_ID` - ID тенанта для мультитенантного Loki
- `LOKI_BEARER_TOKEN` - Bearer токен для аутентификации
- `LOKI_BEARER_TOKEN_FILE` - Файл содержащий bearer токен
- `LOKI_CA_FILE` - Пользовательский CA файл для TLS
- `LOKI_CERT_FILE` - Файл клиентского сертификата для TLS
- `LOKI_KEY_FILE` - Файл клиентского ключа для TLS

## Ресурсы

- [GitHub Repository](https://github.com/ghrud92/simple-loki-mcp)

## Примечания

Требует Node.js v16 или выше. При наличии использует Grafana Loki logcli если доступен в PATH, иначе автоматически переключается на HTTP API. Поддерживает конфигурационные файлы в формате YAML для настроек аутентификации.