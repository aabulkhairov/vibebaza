---
title: Prometheus (TypeScript) MCP сервер
description: Model Context Protocol (MCP) сервер, который обеспечивает бесшовную интеграцию
  с Prometheus, позволяя AI-ассистентам запрашивать метрики, находить доступные данные
  и анализировать производительность системы через естественный язык.
tags:
- Monitoring
- DevOps
- Analytics
- API
author: Community
featured: false
---

Model Context Protocol (MCP) сервер, который обеспечивает бесшовную интеграцию с Prometheus, позволяя AI-ассистентам запрашивать метрики, находить доступные данные и анализировать производительность системы через естественный язык.

## Установка

### NPX

```bash
npx prometheus-mcp-server
```

### Глобальная установка

```bash
npm install -g prometheus-mcp-server
```

## Конфигурация

### Использование npx (рекомендуется)

```json
{
  "mcpServers": {
    "prometheus": {
      "command": "npx",
      "args": ["prometheus-mcp-server"],
      "env": {
        "PROMETHEUS_URL": "http://localhost:9090"
      }
    }
  }
}
```

### Использование глобальной установки

```json
{
  "mcpServers": {
    "prometheus": {
      "command": "prometheus-mcp-server",
      "env": {
        "PROMETHEUS_URL": "http://localhost:9090"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `prom_query` | Выполнить мгновенный PromQL запрос - получить текущие значения метрик, статус алертов |
| `prom_range` | Выполнить диапазонный PromQL запрос - анализировать тренды, создавать графики, исторические данные |
| `prom_discover` | Найти доступные метрики - изучить какие метрики доступны в вашей системе |
| `prom_metadata` | Получить метаданные метрик - понять типы метрик, описания и единицы измерения |
| `prom_targets` | Получить информацию о целях сбора - мониторить здоровье scraping'а и service discovery |

## Возможности

- Доступ к метрикам в реальном времени - запрашивайте текущие и исторические данные метрик
- Обнаружение метрик - находите доступные метрики и цели мониторинга
- Множественные методы аутентификации - базовая аутентификация, bearer токены и поддержка TLS
- Типобезопасность - полная реализация на TypeScript

## Переменные окружения

### Обязательные
- `PROMETHEUS_URL` - URL сервера Prometheus

### Опциональные
- `PROMETHEUS_USERNAME` - Имя пользователя для базовой аутентификации
- `PROMETHEUS_PASSWORD` - Пароль для базовой аутентификации
- `PROMETHEUS_TOKEN` - Bearer токен для аутентификации
- `PROMETHEUS_TIMEOUT` - Таймаут соединения в миллисекундах
- `PROMETHEUS_INSECURE` - Разрешить небезопасные соединения (для самоподписанных сертификатов)

## Примеры использования

```
What's the current CPU usage across all servers?
```

```
Show me HTTP request rates for the last 6 hours
```

```
Which services have the highest memory consumption?
```

```
Are there any failing health checks?
```

```
What metrics are available for monitoring my database?
```

## Ресурсы

- [GitHub Repository](https://github.com/yanmxa/prometheus-mcp-server)

## Примечания

Поддерживает множественные методы аутентификации, включая отсутствие аутентификации, базовую аутентификацию и bearer токены. Для окружений разработки можно включить небезопасные соединения для самоподписанных сертификатов.