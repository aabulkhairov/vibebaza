---
title: Thales CDSP CRDP MCP сервер
description: MCP сервер для безопасной защиты и раскрытия данных через сервис Thales CipherTrust RestFul Data Protection (CRDP), поддерживающий как индивидуальные, так и массовые операции с версионированием.
tags:
- Security
- API
- Database
- Integration
- Analytics
author: sanyambassi
featured: false
---

MCP сервер для безопасной защиты и раскрытия данных через сервис Thales CipherTrust RestFul Data Protection (CRDP), поддерживающий как индивидуальные, так и массовые операции с версионированием.

## Установка

### Из исходного кода

```bash
git clone https://github.com/sanyambassi/thales-cdsp-crdp-mcp-server.git
cd thales-cdsp-crdp-mcp-server
npm install
npm run build
npm start
```

### HTTP транспорт

```bash
MCP_TRANSPORT=streamable-http npm start
```

## Конфигурация

### Интеграция с AI ассистентом

```json
{
  "mcpServers": {
    "crdp": {
      "command": "node",
      "args": ["/path/to/your/crdp-mcp-server/dist/crdp-mcp-server.js"],
      "env": {
        "CRDP_SERVICE_URL": "http://your-crdp-server:8090",
        "CRDP_PROBES_URL": "http://your-crdp-server:8080",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `protect_data` | Защита отдельного фрагмента чувствительных данных с помощью политик защиты CRDP |
| `protect_bulk` | Защита нескольких элементов данных в одной пакетной операции |
| `reveal_data` | Раскрытие одного фрагмента защищенных данных с соответствующей авторизацией |
| `reveal_bulk` | Раскрытие нескольких защищенных элементов данных в одной пакетной операции |
| `get_metrics` | Получение метрик сервиса CRDP |
| `check_health` | Проверка состояния здоровья сервиса CRDP |
| `check_liveness` | Проверка активности сервиса CRDP |

## Возможности

- Защита данных с использованием политик защиты данных, определенных в Thales CipherTrust менеджере
- Раскрытие данных с безопасной авторизацией (username/jwt)
- Массовые операции для обработки нескольких элементов данных в одной пакетной операции
- Поддержка версионирования для внешних версионных, внутренних версионных политик защиты и политик с отключенным версионированием
- Мониторинг с проверками здоровья и сбором метрик
- Поддержка нескольких транспортов для stdio и HTTP соединений

## Переменные окружения

### Опциональные
- `CRDP_SERVICE_URL` - Эндпоинт сервиса CRDP для операций защиты/раскрытия
- `CRDP_PROBES_URL` - Эндпоинт сервиса CRDP для операций мониторинга
- `MCP_TRANSPORT` - Тип транспорта (stdio или streamable-http)
- `MCP_PORT` - HTTP порт при использовании streamable-http транспорта

## Примеры использования

```
Защитить мой email адрес john.doe@example.com используя email_policy
```

```
Раскрыть защищенные данные abc123def456 для пользователя admin используя политику защиты ssn_policy
```

```
Проверить здоровье моего CRDP сервиса
```

## Ресурсы

- [GitHub Repository](https://github.com/sanyambassi/thales-cdsp-crdp-mcp-server)

## Примечания

Требует Node.js v18+, TypeScript и запущенный CRDP контейнер, зарегистрированный в CipherTrust Manager. Поддерживает интеграцию с Cursor AI, Google Gemini и Claude Desktop. Включает шаблоны n8n workflow для интерфейсов разговорного AI. Поддерживает только CRDP, работающий в режиме no-tls.