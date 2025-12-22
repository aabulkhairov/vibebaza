---
title: KubeSphere MCP сервер
description: 'MCP сервер, обеспечивающий интеграцию с KubeSphere API и позволяющий управлять ресурсами через четыре модуля: управление рабочими пространствами, управление кластерами, управление пользователями и ролями, а также центр расширений.'
tags:
- Cloud
- DevOps
- API
- Integration
- Monitoring
author: kubesphere
featured: false
---

MCP сервер, обеспечивающий интеграцию с KubeSphere API и позволяющий управлять ресурсами через четыре модуля: управление рабочими пространствами, управление кластерами, управление пользователями и ролями, а также центр расширений.

## Установка

### Из исходного кода

```bash
go build -o ks-mcp-server cmd/main.go
```

### Релизы GitHub

```bash
Download from https://github.com/kubesphere/ks-mcp-server/releases and move to $PATH
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "KubeSphere": {
      "args": [
        "stdio",
        "--ksconfig", "<ksconfig file absolute path>",
        "--ks-apiserver", "<KubeSphere Address>"
      ],
      "command": "ks-mcp-server"
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "KubeSphere": {
      "args": [
        "stdio",
        "--ksconfig", "<ksconfig file absolute path>",
        "--ks-apiserver", "<KubeSphere Address>"
      ],
      "command": "ks-mcp-server"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `Workspace Management` | Управление рабочими пространствами KubeSphere |
| `Cluster Management` | Управление кластерами KubeSphere |
| `User and Roles` | Управление пользователями и контролем доступа на основе ролей |
| `Extensions Center` | Управление расширениями KubeSphere |

## Возможности

- Интеграция с KubeSphere API
- Управление ресурсами через четыре модуля инструментов
- Поддержка как HTTP, так и HTTPS соединений
- Конфигурация через KSConfig файл, аналогично kubeconfig

## Переменные окружения

### Опциональные
- `KUBESPHERE_CONTEXT` - Изменение контекста по умолчанию для KubeSphere (по умолчанию: kubesphere)

## Ресурсы

- [GitHub Repository](https://github.com/kubesphere/ks-mcp-server)

## Примечания

Требуется кластер KubeSphere с адресом доступа, именем пользователя и паролем. Необходимо сгенерировать KSConfig файл в формате YAML, содержащий детали подключения к кластеру. Поддерживается опциональный CA сертификат для HTTPS доступа.