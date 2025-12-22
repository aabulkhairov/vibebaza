---
title: VMware Fusion MCP сервер
description: MCP сервер для управления виртуальными машинами VMware Fusion через Fusion REST API, предоставляющий операции питания, список VM и получение информации.
tags:
- DevOps
- Cloud
- API
- Productivity
- Integration
author: Community
featured: false
---

MCP сервер для управления виртуальными машинами VMware Fusion через Fusion REST API, предоставляющий операции питания, список VM и получение информации.

## Установка

### Из исходников

```bash
git clone https://github.com/yeahdongcn/vmware-fusion-mcp-server.git
cd vmware-fusion-mcp-server
make env
```

### uvx

```bash
uvx vmware-fusion-mcp-server
```

## Конфигурация

### VS Code

```json
{
  "mcpServers": {
    "vmware-fusion": {
      "command": "uvx",
      "args": ["vmware-fusion-mcp-server"],
      "env": {
        "VMREST_USER": "your-username",
        "VMREST_PASS": "your-password"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_vms` | Список всех VM в VMware Fusion |
| `get_vm_info` | Получение детальной информации о конкретной VM |
| `power_vm` | Выполнение действий с питанием VM (включение, выключение, приостановка, пауза, снятие с паузы, перезагрузка) |
| `get_vm_power_state` | Получение состояния питания конкретной VM |

## Возможности

- Список VM: Просмотр всех виртуальных машин, зарегистрированных в VMware Fusion
- Информация о VM: Получение детальной информации о конкретной виртуальной машине
- Операции с питанием: Выполнение действий с питанием (включение, выключение, приостановка, пауза, снятие с паузы, перезагрузка) VM
- Получение состояния питания: Запрос текущего состояния питания VM
- Современная интеграция с MCP/LLM: Предоставляет все функции как MCP инструменты для LLM и агентских фреймворков

## Переменные окружения

### Обязательные
- `VMREST_USER` - Имя пользователя для vmrest API
- `VMREST_PASS` - Пароль для vmrest API

## Ресурсы

- [GitHub Repository](https://github.com/yeahdongcn/vmware-fusion-mcp-server)

## Примечания

Требует VMware Fusion Pro с включенным REST API и запущенным сервисом vmrest на localhost:8697. Построен с использованием фреймворка FastMCP.