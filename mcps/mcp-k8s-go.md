---
title: mcp-k8s-go MCP сервер
description: MCP сервер на Golang для подключения к кластерам Kubernetes. Позволяет просматривать, управлять и мониторить ресурсы Kubernetes, включая поды, сервисы, деплойменты, логи и события.
tags:
- DevOps
- Cloud
- Monitoring
- API
author: strowk
featured: true
install_command: npx -y @smithery/cli install @strowk/mcp-k8s --client claude
---

MCP сервер на Golang для подключения к кластерам Kubernetes. Позволяет просматривать, управлять и мониторить ресурсы Kubernetes, включая поды, сервисы, деплойменты, логи и события.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @strowk/mcp-k8s --client claude
```

### mcp-get

```bash
npx @michaellatman/mcp-get@latest install @strowk/mcp-k8s
```

### NPM Global

```bash
npm install -g @strowk/mcp-k8s
```

### NPX

```bash
npx @strowk/mcp-k8s
```

### Из исходников

```bash
go get github.com/strowk/mcp-k8s-go
go install github.com/strowk/mcp-k8s-go
```

## Конфигурация

### Claude Desktop (NPM)

```json
{
  "mcpServers": {
    "mcp_k8s": {
      "command": "mcp-k8s",
      "args": []
    }
  }
}
```

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "mcp_k8s": {
      "command": "npx",
      "args": [
        "@strowk/mcp-k8s"
      ]
    }
  }
}
```

### Claude Desktop (Binary)

```json
{
  "mcpServers": {
    "mcp_k8s": {
      "command": "mcp-k8s-go",
      "args": []
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "mcp_k8s_go": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "-v",
        "~/.kube/config:/home/nonroot/.kube/config",
        "--rm",
        "mcpk8s/server:latest"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `list_contexts` | Список контекстов Kubernetes |
| `list_namespaces` | Список неймспейсов Kubernetes |
| `list_resources` | Список, получение, создание и изменение любых ресурсов Kubernetes |
| `list_nodes` | Список узлов Kubernetes |
| `get_events` | Получение событий Kubernetes |
| `get_pod_logs` | Получение логов подов Kubernetes |
| `exec_pod_command` | Выполнение команд в подах Kubernetes |

## Возможности

- Список контекстов Kubernetes
- Список неймспейсов Kubernetes
- Список, получение, создание и изменение любых ресурсов Kubernetes с пользовательскими маппингами для подов, сервисов, деплойментов
- Список узлов Kubernetes
- Список подов Kubernetes
- Получение событий Kubernetes
- Получение логов подов Kubernetes
- Выполнение команд в подах Kubernetes
- Поддержка режима только для чтения для предотвращения изменений в кластере
- Настраиваемые разрешенные контексты для безопасности

## Переменные окружения

### Опциональные
- `KUBECONFIG` - Путь к файлу конфигурации Kubernetes

## Примеры использования

```
Check pod logs for errors in kube-system namespace
```

## Ресурсы

- [GitHub Repository](https://github.com/strowk/mcp-k8s-go)

## Примечания

Опции командной строки включают: --allowed-contexts для ограничения доступа к определенным контекстам, --readonly для отключения операций записи, --mask-secrets для управления маскированием секретов (по умолчанию: true), --help и --version. Доступны мультиархитектурные Docker образы для linux/amd64 и linux/arm64.