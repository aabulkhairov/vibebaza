---
title: Kubernetes MCP сервер
description: MCP сервер для подключения к Kubernetes кластеру и управления им, с поддержкой kubeconfig из различных источников и полным набором kubectl операций.
tags:
- DevOps
- Cloud
- Monitoring
- Code
- API
author: Community
featured: false
install_command: claude mcp add kubernetes -- npx mcp-server-kubernetes
---

MCP сервер для подключения к Kubernetes кластеру и управления им, с поддержкой kubeconfig из различных источников и полным набором kubectl операций.

## Установка

### NPX

```bash
npx mcp-server-kubernetes
```

### Claude Code

```bash
claude mcp add kubernetes -- npx mcp-server-kubernetes
```

### mcpb Extension

```bash
Download .mcpb from latest Release or install via Claude Desktop Extensions
```

### Gemini CLI

```bash
gemini extensions install https://github.com/Flux159/mcp-server-kubernetes
```

### Из исходного кода

```bash
git clone https://github.com/Flux159/mcp-server-kubernetes.git
cd mcp-server-kubernetes
bun install
bun run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "npx",
      "args": ["mcp-server-kubernetes"]
    }
  }
}
```

### Claude Desktop неразрушающий режим

```json
{
  "mcpServers": {
    "kubernetes-readonly": {
      "command": "npx",
      "args": ["mcp-server-kubernetes"],
      "env": {
        "ALLOW_ONLY_NON_DESTRUCTIVE_TOOLS": "true"
      }
    }
  }
}
```

### VS Code

```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "npx",
      "args": ["mcp-server-kubernetes"],
      "description": "Kubernetes cluster management and operations"
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "npx",
      "args": ["mcp-server-kubernetes"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `kubectl_get` | Получить или перечислить ресурсы Kubernetes |
| `kubectl_describe` | Подробное описание ресурсов Kubernetes |
| `kubectl_create` | Создать ресурсы Kubernetes |
| `kubectl_apply` | Применить YAML манифесты к кластеру |
| `kubectl_delete` | Удалить ресурсы Kubernetes |
| `kubectl_logs` | Получить логи из подов и контейнеров |
| `kubectl_context` | Управление контекстами kubectl |
| `explain_resource` | Объяснить ресурсы Kubernetes и их поля |
| `list_api_resources` | Перечислить доступные API ресурсы в кластере |
| `kubectl_scale` | Масштабировать деплойменты и другие масштабируемые ресурсы |
| `kubectl_patch` | Обновить поле(я) ресурса |
| `kubectl_rollout` | Управление развертываниями деплойментов |
| `kubectl_generic` | Выполнить любую команду kubectl |
| `ping` | Проверить соединение с Kubernetes кластером |
| `port_forward` | Проброс портов к подам и сервисам |

## Возможности

- Подключение к Kubernetes кластеру с поддержкой kubeconfig
- Единый kubectl API для управления всеми типами ресурсов
- Продвинутые операции включая масштабирование, проброс портов и развертывания
- Полная поддержка операций Helm с альтернативами на основе шаблонов
- Операции очистки подов для проблемных подов
- Операции управления нодами для обслуживания и масштабирования
- Систематический процесс диагностики с промптом k8s-diagnose
- Неразрушающий режим только для чтения и операций создания/обновления
- Маскирование секретов для безопасности

## Переменные окружения

### Опциональные
- `ALLOW_ONLY_NON_DESTRUCTIVE_TOOLS` - Включить неразрушающий режим, который отключает все разрушительные операции

## Примеры использования

```
List all pods in the current namespace
```

```
Create a test deployment
```

```
Scale a deployment to 3 replicas
```

```
Get logs from a specific pod
```

```
Apply a YAML manifest to the cluster
```

## Ресурсы

- [GitHub Repository](https://github.com/Flux159/mcp-server-kubernetes)

## Примечания

Требуется установленный kubectl с настроенным kubeconfig файлом. Helm v3 опционален, но необходим для операций Helm. Сервер загружает kubeconfig из ~/.kube/config по умолчанию. Неразрушающий режим можно включить для предотвращения любых разрушительных операций при сохранении полных возможностей чтения и создания/обновления.