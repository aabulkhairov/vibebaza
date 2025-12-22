---
title: Kubernetes and OpenShift MCP сервер
description: Мощная и гибкая реализация Kubernetes MCP сервера с поддержкой
  Kubernetes и OpenShift, предоставляющая нативные операции на Go без внешних
  зависимостей.
tags:
- DevOps
- Cloud
- Monitoring
- Integration
- API
author: containers
featured: true
---

Мощная и гибкая реализация Kubernetes MCP сервера с поддержкой Kubernetes и OpenShift, предоставляющая нативные операции на Go без внешних зависимостей.

## Установка

### NPX

```bash
npx -y kubernetes-mcp-server@latest
```

### UVX

```bash
uvx kubernetes-mcp-server@latest
```

### VS Code CLI

```bash
code --add-mcp '{"name":"kubernetes","command":"npx","args":["kubernetes-mcp-server@latest"]}'
```

### VS Code Insiders CLI

```bash
code-insiders --add-mcp '{"name":"kubernetes","command":"npx","args":["kubernetes-mcp-server@latest"]}'
```

### Скачивание бинарного файла

```bash
./kubernetes-mcp-server --help
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "npx",
      "args": [
        "-y",
        "kubernetes-mcp-server@latest"
      ]
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "kubernetes-mcp-server": {
      "command": "npx",
      "args": ["-y", "kubernetes-mcp-server@latest"]
    }
  }
}
```

### Goose CLI

```json
extensions:
  kubernetes:
    command: npx
    args:
      - -y
      - kubernetes-mcp-server@latest
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `configuration_contexts_list` | Получить список всех доступных имен контекстов и связанных с ними URL серверов из файла kubeconfig |
| `configuration_view` | Получить текущее содержимое конфигурации Kubernetes в виде kubeconfig YAML |
| `events_list` | Получить список всех событий Kubernetes |
| `pod_list` | Получить список подов во всех неймспейсах или в конкретном неймспейсе |
| `pod_get` | Получить под по имени из указанного неймспейса |
| `pod_delete` | Удалить под по имени из указанного неймспейса |
| `pod_logs` | Показать логи пода по имени из указанного неймспейса |
| `pod_top` | Получить метрики использования ресурсов для всех подов или конкретного пода в указанном неймспейсе |
| `pod_exec` | Выполнить команду внутри пода |
| `pod_run` | Запустить образ контейнера в поде и опционально экспонировать его |
| `namespace_list` | Получить список неймспейсов Kubernetes |
| `project_list` | Получить список проектов OpenShift |
| `helm_install` | Установить Helm чарт в текущий или указанный неймспейс |
| `helm_list` | Получить список релизов Helm во всех неймспейсах или в конкретном неймспейсе |
| `helm_uninstall` | Удалить релиз Helm в текущем или указанном неймспейсе |

## Возможности

- Автоматическое обнаружение изменений в конфигурации Kubernetes и обновление MCP сервера
- Просмотр и управление текущей конфигурацией Kubernetes .kube/config или внутрикластерной конфигурацией
- Выполнение CRUD операций с любыми ресурсами Kubernetes или OpenShift
- Специализированные операции с подами включая логи, exec, top, run и управление
- Список неймспейсов Kubernetes и проектов OpenShift
- Просмотр событий Kubernetes во всех неймспейсах или в конкретном неймспейсе
- Управление Helm чартами (установка, список, удаление)
- Нативная реализация на Go без внешних зависимостей
- Легковесное распространение в виде одного бинарного файла для Linux, macOS и Windows
- Высокопроизводительное/низколатентное прямое взаимодействие с API сервером

## Примеры использования

```
Диагностировать и автоматически исправить развертывание OpenShift
```

```
Получить список всех подов в неймспейсе по умолчанию
```

```
Показать логи для конкретного пода
```

```
Развернуть Helm чарт в кластер
```

```
Просмотреть события Kubernetes для устранения неполадок
```

## Ресурсы

- [GitHub Repository](https://github.com/manusa/kubernetes-mcp-server)

## Примечания

В отличие от других реализаций Kubernetes MCP серверов, это НЕ просто обертка вокруг инструментов командной строки kubectl или helm. Требуется доступ к кластеру Kubernetes и поддерживает наборы инструментов (config, core, helm, kiali), которые можно включить/отключить через флаг --toolsets. Опции конфигурации включают --port, --log-level, --kubeconfig, --list-output, --read-only, --disable-destructive, --toolsets и --disable-multi-cluster.