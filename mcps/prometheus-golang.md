---
title: Prometheus (Golang) MCP сервер
description: MCP сервер, который позволяет LLM взаимодействовать с инстансами Prometheus через API для генерации и выполнения PromQL запросов, анализа метрик, управления конфигурациями и доступа к полным возможностям мониторинга.
tags:
- Monitoring
- DevOps
- Analytics
- API
- Database
author: Community
featured: false
---

MCP сервер, который позволяет LLM взаимодействовать с инстансами Prometheus через API для генерации и выполнения PromQL запросов, анализа метрик, управления конфигурациями и доступа к полным возможностям мониторинга.

## Установка

### Бинарный файл

```bash
/path/to/prometheus-mcp-server <flags>

# или используя переменные окружения
PROMETHEUS_MCP_SERVER_PROMETHEUS_URL="https://$yourPrometheus:9090" /path/to/prometheus-mcp-server
```

### Docker (Stdio)

```bash
docker run --rm -i ghcr.io/tjhop/prometheus-mcp-server:latest --prometheus.url "https://$yourPrometheus:9090"

# или используя переменные окружения
docker run --rm -i -e PROMETHEUS_MCP_SERVER_PROMETHEUS_URL="https://$yourPrometheus:9090" ghcr.io/tjhop/prometheus-mcp-server:latest
```

### Docker (HTTP)

```bash
docker run --rm -p 8080:8080 ghcr.io/tjhop/prometheus-mcp-server:latest --prometheus.url "https://$yourPrometheus:9090" --mcp.transport "http" --web.listen-address ":8080"

# или используя переменные окружения
docker run --rm -p 8080:8080 -e PROMETHEUS_MCP_SERVER_PROMETHEUS_URL="https://$yourPrometheus:9090" -e PROMETHEUS_MCP_SERVER_MCP_TRANSPORT="http" -e PROMETHEUS_MCP_SERVER_WEB_LISTEN_ADDRESS=":8080" ghcr.io/tjhop/prometheus-mcp-server:latest
```

### Системный пакет

```bash
apt install /path/to/package
systemctl edit prometheus-mcp-server.service
systemctl enable --now prometheus-mcp-server.service
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `alertmanagers` | Получить обзор обнаружения Prometheus Alertmanager |
| `build_info` | Получить информацию о сборке Prometheus |
| `config` | Получить конфигурацию Prometheus |
| `docs_list` | Список официальных документационных файлов Prometheus |
| `docs_read` | Читает названный markdown файл, содержащий официальную документацию Prometheus из репозитория prometheus/doc... |
| `docs_search` | Поиск по markdown файлам, содержащим официальную документацию Prometheus из репозитория prometheus/docs |
| `exemplars_query` | Выполняет запрос примеров по заданному запросу и временному диапазону |
| `flags` | Получить флаги времени выполнения |
| `healthy` | Управленческий API эндпоинт, который можно использовать для проверки состояния Prometheus |
| `label_names` | Возвращает уникальные имена лейблов, присутствующие в блоке в отсортированном порядке по заданному временному диапазону и матчерам |
| `label_values` | Выполняет запрос значений для заданного лейбла, временного диапазона и матчеров |
| `list_alerts` | Перечислить все активные алерты |
| `list_rules` | Перечислить все правила оповещений и записи, которые загружены |
| `list_targets` | Получить обзор обнаружения целей Prometheus |
| `metric_metadata` | Возвращает метаданные о метриках, которые в настоящее время собираются по имени метрики |

## Возможности

- Полная поддержка Prometheus HTTP API с выводом данных в формате JSON
- Поддержка формата Token-Oriented Object Notation (TOON) для эффективности токенов
- Поддержка множественных Prometheus-совместимых бэкендов (Thanos, Mimir, Cortex)
- TSDB Admin API эндпоинты для продвинутых операций (с флагом безопасности)
- Возможности поиска и чтения официальной документации Prometheus
- Поддержка безопасного подключения с HTTP конфигурационными файлами
- Множественные режимы транспорта: STDIO, SSE и HTTP
- Встроенная телеметрия и экспозиция Prometheus метрик
- Конфигурируемые наборы инструментов для меньших контекстных окон
- Поддержка аутентификации и TLS через веб-конфигурационные файлы

## Переменные окружения

### Обязательные
- `PROMETHEUS_MCP_SERVER_PROMETHEUS_URL` - URL инстанса Prometheus для подключения

### Опциональные
- `PROMETHEUS_MCP_SERVER_MCP_TRANSPORT` - Режим транспорта для MCP сервера
- `PROMETHEUS_MCP_SERVER_WEB_LISTEN_ADDRESS` - Адрес и порт для прослушивания веб-сервера

## Примеры использования

```
use the tools from the prometheus mcp server to investigate the metrics from the mcp server and suggest prometheus recording rules for SLOs
```

```
summarize prometheus metric/label name best practices
```

```
please provide a comprehensive review and summary of the prometheus server. review it's configuration, flags, runtime/build info, and anything else that you feel may provide insight into the status of the prometheus instance, including analyzing metrics and executing queries
```

## Ресурсы

- [GitHub Repository](https://github.com/tjhop/prometheus-mcp-server)

## Примечания

Поддерживает Prometheus совместимые бэкенды, такие как Thanos, Mimir и Cortex с настройками инструментов, специфичными для бэкенда. TSDB Admin API инструменты требуют флаг --dangerous.enable-tsdb-admin-tools для безопасности. Включает файлы сервиса systemd в системных пакетах. Экспонирует метрики телеметрии для мониторинга самого MCP сервера.