---
title: MCP-Ambari-API MCP сервер
description: MCP сервер для управления кластерами Apache Ambari с помощью ИИ через команды на естественном языке, обеспечивающий автоматизированные операции кластера Hadoop, мониторинг сервисов, инспекцию конфигурации и запросы метрик.
tags:
- DevOps
- Monitoring
- Analytics
- API
- Integration
author: call518
featured: false
---

MCP сервер для управления кластерами Apache Ambari с помощью ИИ через команды на естественном языке, обеспечивающий автоматизированные операции кластера Hadoop, мониторинг сервисов, инспекцию конфигурации и запросы метрик.

## Установка

### Docker Compose

```bash
# Clone repository
git clone https://github.com/call518/MCP-Ambari-API.git
cd MCP-Ambari-API

# Copy environment template and configure
cp .env.example .env
# Edit .env with your Ambari cluster information

# Run with Docker Compose
docker-compose up -d
```

### Python CLI (stdio режим)

```bash
python -m mcp_ambari_api --type stdio
```

### Python CLI (HTTP режим)

```bash
python -m mcp_ambari_api --type streamable-http --host 0.0.0.0 --port 8000
```

### Python CLI (с аутентификацией)

```bash
python -m mcp_ambari_api --type streamable-http --auth-enable --secret-key your-secure-secret-key-here
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_common_metrics_catalog` | Поиск по ключевым словам в каталоге метрик с живыми метаданными для обнаружения доступных метрик |
| `list_ambari_metric_apps` | Список обнаруженных значений AMS appId с опциональным подсчетом метрик и возможностью обновления |
| `list_ambari_metrics_metadata` | Исследователь сырых метаданных AMS с поддержкой фильтрации по app_id, метрикам и хостам |
| `query_ambari_metrics` | Получение данных временных рядов с автоматически выбранными именами метрик и контролем точности |
| `hdfs_dfadmin_report` | Генерация отчетов о емкости и сводки DataNode в стиле DFSAdmin |

## Возможности

- Интерактивный центр операций Ambari для управления кластером на естественном языке
- Видимость кластера в реальном времени со статусом сервисов, деталями хостов и историей оповещений
- Интеллектуальный пайплайн метрик с динамическими AMS appIds и обнаружением имен метрик
- Автоматизированный рабочий процесс операций для запуска/остановки и проверки конфигураций
- Встроенные операционные отчеты, включая отчеты HDFS и метрики емкости
- Защитные механизмы, требующие подтверждения пользователя для масштабных операций
- Оптимизация интеграции с LLM с примерами на естественном языке
- Гибкие модели развертывания с поддержкой stdio и streamable-http транспорта
- Ориентированная на производительность архитектура кеширования для быстрых ответов
- Аутентификация Bearer токеном для безопасности в продакшене

## Переменные окружения

### Обязательные
- `AMBARI_HOST` - Имя хоста или IP адрес сервера Ambari
- `AMBARI_PORT` - Номер порта сервера Ambari
- `AMBARI_USER` - Имя пользователя для аутентификации на сервере Ambari
- `AMBARI_PASS` - Пароль для аутентификации на сервере Ambari
- `AMBARI_CLUSTER_NAME` - Имя целевого кластера Ambari

### Опциональные
- `AMBARI_METRICS_HOST` - Имя хоста коллектора Ambari Metrics (AMS)
- `AMBARI_METRICS_PORT` - Порт коллектора Ambari Metrics (AMS)
- `FASTMCP_TYPE` - Протокол транспорта MCP (stdio или streamable-http)
- `FASTMCP_HOST` - Адрес привязки HTTP сервера
- `FASTMCP_PORT` - Порт HTTP сервера для MCP коммуникации
- `REMOTE_AUTH_ENABLE` - Включить аутентификацию Bearer токеном для streamable-http режима
- `REMOTE_SECRET_KEY` - Секретный ключ для аутентификации Bearer токеном (обязателен при включенной аутентификации)
- `MCP_LOG_LEVEL` - Уровень детализации логирования сервера (DEBUG, INFO, WARNING, ERROR)

## Примеры использования

```
Show the heap-related metrics available for the NameNode appId
```

```
List every appId currently exposed by AMS
```

```
Give me CPU-related metric metadata under HOST
```

```
Plot the last 30 minutes of jvm.JvmMetrics.MemHeapUsedM for the NameNode
```

```
Compare jvm.JvmMetrics.MemHeapUsedM for DataNode hosts over the past 30 minutes
```

## Ресурсы

- [GitHub Repository](https://github.com/call518/MCP-Ambari-API)

## Примечания

Этот сервер требует наличия существующего кластера Apache Ambari для подключения. Он поддерживает как stdio, так и streamable-http режимы транспорта, при этом Docker Compose является рекомендуемым методом развертывания. Сервер включает защитные механизмы для рискованных операций и предоставляет комплексные возможности запросов метрик через Ambari Metrics Service (AMS).