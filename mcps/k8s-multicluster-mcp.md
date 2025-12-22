---
title: k8s-multicluster-mcp MCP сервер
description: MCP сервер для операций Kubernetes, который предоставляет стандартизированный
  API для одновременного взаимодействия с несколькими кластерами Kubernetes, используя
  множественные kubeconfig файлы.
tags:
- DevOps
- Cloud
- Monitoring
- API
- Integration
author: razvanmacovei
featured: false
---

MCP сервер для операций Kubernetes, который предоставляет стандартизированный API для одновременного взаимодействия с несколькими кластерами Kubernetes, используя множественные kubeconfig файлы.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @razvanmacovei/k8s-multicluster-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/razvanmacovei/k8s-multicluster-mcp.git
cd k8s-multicluster-mcp
python3 -m venv .venv
source .venv/bin/activate  # On macOS/Linux
pip install -r requirements.txt
python3 app.py
```

## Конфигурация

### MCPO Server / Claude Desktop

```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "python3",
      "args": ["/path/to/k8s-multicluster-mcp/app.py"],
      "env": {
        "KUBECONFIG_DIR": "/path/to/your/kubeconfigs"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `k8s_get_contexts` | Получить список всех доступных контекстов Kubernetes |
| `k8s_get_namespaces` | Получить список всех namespace в указанном контексте |
| `k8s_get_nodes` | Получить список всех нод в кластере |
| `k8s_get_resources` | Получить список ресурсов указанного типа |
| `k8s_get_resource` | Получить подробную информацию о конкретном ресурсе |
| `k8s_get_pod_logs` | Получить логи из конкретного пода |
| `k8s_describe` | Показать подробную информацию о конкретном ресурсе или группе ресурсов |
| `k8s_apis` | Получить список всех доступных API в кластере Kubernetes |
| `k8s_crds` | Получить список всех Custom Resource Definitions (CRDs) в кластере |
| `k8s_top_nodes` | Показать использование ресурсов нод |
| `k8s_top_pods` | Показать использование ресурсов подов |
| `k8s_rollout_status` | Получить статус развертывания |
| `k8s_rollout_history` | Получить историю ревизий развертывания |
| `k8s_rollout_undo` | Откатить развертывание к предыдущей ревизии |
| `k8s_rollout_restart` | Перезапустить развертывание |

## Возможности

- Поддержка множественных Kubeconfig файлов - работа с несколькими кластерами
- Выбор контекста - легкое переключение между кластерами
- Межкластерные операции - сравнение ресурсов в разных кластерах
- Централизованное управление - управление всеми окружениями из единого интерфейса
- Управление кластером - список контекстов, namespace, нод и ресурсов
- Управление ресурсами - инспекция подов, деплойментов, сервисов и получение логов
- Метрики и мониторинг - отображение использования CPU/памяти нод и подов
- Управление развертываниями - получение статуса, истории, откат, перезапуск, пауза и возобновление развертываний
- Масштабирование и автомасштабирование ресурсов
- Создание и управление ресурсами с YAML/JSON

## Переменные окружения

### Обязательные
- `KUBECONFIG_DIR` - Путь к директории, содержащей kubeconfig файлы для множественных кластеров

## Примеры использования

```
List all available contexts across my kubeconfig files
```

```
Compare the number of pods running in the 'backend' namespace between my 'prod' and 'staging' contexts
```

```
Show me resource usage across all nodes in my 'dev' and 'prod' clusters
```

```
I have a deployment called 'my-app' in the 'production' namespace that's having issues. Can you check what's wrong?
```

```
I need to scale my 'backend' deployment in the 'default' namespace to 5 replicas
```

## Ресурсы

- [GitHub Repository](https://github.com/razvanmacovei/k8s-multicluster-mcp)

## Примечания

Требует Python 3.8 или выше и менеджер пакетов pip. Поддерживает менеджер пакетов uv для более быстрой установки. Сервер ожидает, что множественные kubeconfig файлы будут размещены в директории, указанной переменной окружения KUBECONFIG_DIR. Каждый kubeconfig файл представляет отдельный кластер Kubernetes.