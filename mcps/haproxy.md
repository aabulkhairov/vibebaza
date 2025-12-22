---
title: HAProxy MCP сервер
description: MCP сервер для HAProxy, написанный на Go, который предоставляет стандартизированный способ для LLM взаимодействовать с runtime API HAProxy и страницей статистики для администрирования, мониторинга и анализа трафика.
tags:
- DevOps
- Monitoring
- API
- Integration
- Analytics
author: Community
featured: false
---

MCP сервер для HAProxy, написанный на Go, который предоставляет стандартизированный способ для LLM взаимодействовать с runtime API HAProxy и страницей статистики для администрирования, мониторинга и анализа трафика.

## Установка

### Homebrew

```bash
# Add the tap
brew tap tuannvm/tap

# Install the package
brew install haproxy-mcp-server
```

### Из бинарного файла

```bash
Download the latest binary for your platform from the releases page
```

### Используя Go

```bash
go install github.com/tuannvm/haproxy-mcp-server/cmd/server@latest
```

### Используя Docker

```bash
docker pull ghcr.io/tuannvm/haproxy-mcp-server:latest
docker run -it --rm \
  -e HAPROXY_HOST=your-haproxy-host \
  -e HAPROXY_PORT=9999 \
  ghcr.io/tuannvm/haproxy-mcp-server:latest
```

## Конфигурация

### HAProxy Runtime API через TCP4

```json
{
  "mcpServers": {
    "haproxy": {
      "command": "haproxy-mcp-server",
      "env": {
        "HAPROXY_HOST": "localhost",
        "HAPROXY_PORT": "9999",
        "HAPROXY_RUNTIME_MODE": "tcp4",
        "HAPROXY_RUNTIME_TIMEOUT": "10",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

### HAProxy Runtime API через Unix Socket

```json
{
  "mcpServers": {
    "haproxy": {
      "command": "haproxy-mcp-server",
      "env": {
        "HAPROXY_RUNTIME_MODE": "unix",
        "HAPROXY_RUNTIME_SOCKET": "/var/run/haproxy/admin.sock",
        "HAPROXY_RUNTIME_TIMEOUT": "10",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

### HAProxy с поддержкой страницы статистики

```json
{
  "mcpServers": {
    "haproxy": {
      "command": "haproxy-mcp-server",
      "env": {
        "HAPROXY_STATS_ENABLED": "true",
        "HAPROXY_STATS_URL": "http://localhost:8404/stats",
        "HAPROXY_STATS_TIMEOUT": "5",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

## Возможности

- Полная поддержка HAProxy Runtime API с исчерпывающим покрытием команд runtime API HAProxy
- Контекстно-зависимые операции с правильной обработкой тайм-аутов и отмены
- Интеграция со страницей статистики для веб-интерфейса статистики HAProxy с расширенными метриками и визуализацией
- Безопасная аутентификация для защищенных подключений к runtime API HAProxy
- Множественные варианты транспорта с поддержкой как stdio, так и HTTP транспортов
- Готовность для предприятий - дизайн для продакшн использования в корпоративных средах
- Поддержка Docker с готовыми Docker образами для простого деплоя

## Переменные окружения

### Опциональные
- `HAPROXY_HOST` - Хост инстанса HAProxy (только для режима TCP4)
- `HAPROXY_PORT` - Порт для HAProxy Runtime API (только для режима TCP4)
- `HAPROXY_RUNTIME_MODE` - Режим подключения: "tcp4" или "unix"
- `HAPROXY_RUNTIME_SOCKET` - Путь к сокету (только для режима Unix)
- `HAPROXY_RUNTIME_URL` - Прямой URL к Runtime API (опционально, переопределяет другие настройки runtime)
- `HAPROXY_RUNTIME_TIMEOUT` - Тайм-аут для операций runtime API в секундах
- `HAPROXY_STATS_ENABLED` - Включить поддержку страницы статистики HAProxy
- `HAPROXY_STATS_URL` - URL к странице статистики HAProxy (например, http://localhost:8404/stats)

## Ресурсы

- [GitHub Repository](https://github.com/tuannvm/haproxy-mcp-server)

## Примечания

Сервер предоставляет инструменты, организованные по категориям: Статистика и информация о процессах, Обнаружение топологии, Динамическое управление пулами, Контроль сессий, Карты и ACL, Проверки состояния и агенты, а также Разнообразные операции. Вы можете использовать Runtime API, Stats API или оба одновременно. Как минимум один из них должен быть правильно настроен для функционирования сервера. См. документацию tools.md и haproxy.md для полного списка инструментов и руководства по конфигурации HAProxy.