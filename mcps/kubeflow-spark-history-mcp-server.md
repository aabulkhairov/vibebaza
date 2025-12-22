---
title: Kubeflow Spark History MCP сервер
description: MCP сервер, который позволяет AI агентам анализировать производительность Apache Spark задач,
  выявлять узкие места и предоставлять умные инсайты на основе данных из Spark History Server.
tags:
- Monitoring
- Analytics
- DevOps
- Cloud
- AI
author: kubeflow
featured: true
---

MCP сервер, который позволяет AI агентам анализировать производительность Apache Spark задач, выявлять узкие места и предоставлять умные инсайты на основе данных из Spark History Server.

## Установка

### PyPI с uvx

```bash
uvx --from mcp-apache-spark-history-server spark-mcp
```

### Установка через Pip

```bash
python3 -m venv spark-mcp && source spark-mcp/bin/activate
pip install mcp-apache-spark-history-server
python3 -m spark_history_mcp.core.main
```

### Из исходников

```bash
git clone https://github.com/kubeflow/mcp-apache-spark-history-server.git
cd mcp-apache-spark-history-server
brew install go-task
task start-spark-bg
task start-mcp-bg
```

### Helm

```bash
helm install spark-history-mcp ./deploy/kubernetes/helm/spark-history-mcp/
```

## Конфигурация

### Конфигурация сервера

```json
servers:
  local:
    default: true
    url: "http://your-spark-history-server:18080"
    auth:
      username: "user"
      password: "pass"
    include_plan_description: false
mcp:
  transports:
    - streamable-http
  port: "18888"
  debug: true
```

### Конфигурация нескольких серверов

```json
servers:
  production:
    default: true
    url: "http://prod-spark-history:18080"
    auth:
      username: "user"
      password: "pass"
  staging:
    url: "http://staging-spark-history:18080"
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_applications` | Получить список всех приложений, доступных на Spark History Server с опциональной фильтрацией по... |
| `get_application` | Получить детальную информацию о конкретном Spark приложении включая статус, использование ресурсов, длительность... |
| `list_jobs` | Получить список всех задач для Spark приложения с опциональной фильтрацией по статусу |
| `list_slowest_jobs` | Получить N самых медленных задач для Spark приложения (исключает запущенные задачи по умолчанию) |
| `list_stages` | Получить список всех стадий для Spark приложения с опциональной фильтрацией по статусу и сводками |
| `list_slowest_stages` | Получить N самых медленных стадий для Spark приложения (исключает запущенные стадии по умолчанию) |
| `get_stage` | Получить информацию о конкретной стадии с опциональным ID попытки и сводными метриками |
| `get_stage_task_summary` | Получить статистические распределения метрик задач для конкретной стадии (время выполнения, использование памяти... |
| `list_executors` | Получить информацию об исполнителях с опциональным включением неактивных исполнителей |
| `get_executor` | Получить информацию о конкретном исполнителе включая распределение ресурсов, статистику задач и производительность... |
| `get_executor_summary` | Агрегирует метрики по всем исполнителям (использование памяти, дискового пространства, количество задач, метрики производительности) |
| `get_resource_usage_timeline` | Получить хронологическое представление паттернов распределения и использования ресурсов включая добавление/удаление исполнителей... |
| `get_environment` | Получить комплексную конфигурацию среды выполнения Spark включая информацию о JVM, свойства Spark, системные свойства... |
| `list_slowest_sql_queries` | Получить топ N самых медленных SQL запросов для приложения с детальными метриками выполнения и опциональными... |
| `compare_sql_execution_plans` | Сравнить планы выполнения SQL между двумя Spark задачами, анализируя логические/физические планы и выполнение... |

## Возможности

- Запросы информации о задачах через естественный язык
- Анализ метрик производительности по приложениям
- Сравнение нескольких задач для выявления регрессий
- Исследование сбоев с детальным анализом ошибок
- Генерация инсайтов на основе исторических данных выполнения
- Поддержка нескольких Spark History Server
- Руководства по интеграции с AWS Glue и EMR
- Деплой в Kubernetes с помощью Helm
- Режимы HTTP и STDIO транспорта

## Переменные окружения

### Опциональные
- `SHS_MCP_PORT` - Порт для MCP сервера
- `SHS_MCP_DEBUG` - Включить режим отладки
- `SHS_MCP_ADDRESS` - Адрес для MCP сервера
- `SHS_MCP_TRANSPORT` - Режим MCP транспорта
- `SHS_MCP_CONFIG` - Путь к файлу конфигурации
- `SHS_SERVERS_*_URL` - URL для конкретного сервера
- `SHS_SERVERS_*_AUTH_USERNAME` - Имя пользователя для конкретного сервера
- `SHS_SERVERS_*_AUTH_PASSWORD` - Пароль для конкретного сервера

## Примеры использования

```
Покажи все приложения между 12 ночи и 1 утра 27 июня 2025
```

```
Почему моя задача медленная?
```

```
Сравни сегодня с вчера
```

```
Что не так со стадией 5?
```

```
Покажи использование ресурсов во времени
```

## Ресурсы

- [GitHub Repository](https://github.com/kubeflow/mcp-apache-spark-history-server)

## Примечания

Требует запущенного и доступного Spark History Server. Необходим Python 3.12+. Пакет опубликован в PyPI. Включает образцы данных для тестирования. Поддерживает HTTP и STDIO транспорты. Совместим с Claude Desktop, Amazon Q CLI, LangGraph и другими MCP клиентами.