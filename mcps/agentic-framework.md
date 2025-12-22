---
title: Agentic Framework MCP сервер
description: MCP фреймворк для коллаборации нескольких AI агентов через асинхронный
  обмен сообщениями. Регистрация агентов, их обнаружение и broadcast-возможности с
  файловым хранилищем.
tags:
- Messaging
- AI
- Integration
- DevOps
- API
author: Piotr1215
featured: false
---

MCP фреймворк для коллаборации нескольких AI агентов через асинхронный обмен сообщениями. Регистрация агентов, их обнаружение и broadcast-возможности с файловым хранилищем.

## Установка

### Из исходников

```bash
git clone https://github.com/Piotr1215/mcp-agentic-framework.git
cd mcp-agentic-framework
npm install
```

### HTTP сервер

```bash
npm run start:http
```

### Kubernetes деплой

```bash
cd /home/decoder/dev/mcp-agentic-framework
vim Justfile  # Change docker_user to your Docker Hub username
just update
```

## Конфигурация

### Claude Desktop HTTP

```json
{
  "mcpServers": {
    "agentic-framework": {
      "type": "http",
      "url": "http://127.0.0.1:3113/mcp"
    }
  }
}
```

### Claude Desktop Kubernetes

```json
"agentic-framework": {
  "type": "http",
  "url": "http://YOUR_LOADBALANCER_IP:3113/mcp"
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `register-agent` | Зарегистрировать нового агента с именем, описанием и опциональным instanceId |
| `unregister-agent` | Удалить агента из системы по ID |
| `discover-agents` | Список всех зарегистрированных агентов с их статусом и активностью |
| `send-message` | Отправить сообщение от одного агента другому |
| `check-for-messages` | Получить непрочитанные сообщения агента (удаляются после прочтения) |
| `update-agent-status` | Обновить статус агента (online, offline, busy, away) |
| `send-broadcast` | Отправить broadcast сообщение всем агентам кроме отправителя с уровнями приоритета |
| `get-pending-notifications` | Получить ожидающие уведомления агента |

## Возможности

- Динамическая регистрация и обнаружение агентов
- Асинхронный двунаправленный обмен сообщениями между агентами
- Broadcast сообщения с уровнями приоритета
- Файловое хранилище для простоты и портативности
- HTTP транспорт с поддержкой Server-Sent Events (SSE)
- Kubernetes деплой с zero-downtime обновлениями
- Health checks и эндпоинты мониторинга
- Автоматическое управление версиями с semantic versioning
- Web UI для мониторинга коммуникации агентов
- Персистентный LoadBalancer IP через MetalLB

## Примеры использования

```
Register an orchestrator agent for coordinating tasks
```

```
Register worker1 agent for processing
```

```
Send message from orchestrator to worker1: Process customer data
```

```
Send broadcast from orchestrator: All tasks completed
```

```
Emergency: System overload detected, pause all operations
```

## Ресурсы

- [GitHub Repository](https://github.com/Piotr1215/mcp-agentic-framework)

## Примечания

Хранит данные в /tmp/mcp-agentic-framework/ с agents.json для реестра и отдельными файлами сообщений. Включает функции безопасности: валидация ввода и файловая блокировка. Health эндпоинт доступен по /health. Сообщения автоматически удаляются после прочтения (одноразовое потребление).
