---
title: MCP-Airflow-API MCP сервер
description: MCP сервер, который превращает операции Apache Airflow REST API в инструменты естественного языка, обеспечивая интуитивное управление кластерами Airflow через разговорные команды вместо сложных вызовов API.
tags:
- DevOps
- API
- Monitoring
- Integration
- Analytics
author: call518
featured: false
---

MCP сервер, который превращает операции Apache Airflow REST API в инструменты естественного языка, обеспечивая интуитивное управление кластерами Airflow через разговорные команды вместо сложных вызовов API.

## Установка

### PyPI с uvx

```bash
uvx --python 3.12 mcp-airflow-api
```

### Docker Compose

```bash
git clone https://github.com/call518/MCP-Airflow-API.git
cd MCP-Airflow-API
cp .env.example .env
# Edit .env with your Airflow API settings
docker-compose up -d
```

### Установка для разработки

```bash
git clone https://github.com/call518/MCP-Airflow-API.git
cd MCP-Airflow-API
pip install -e .
python -m mcp_airflow_api
```

## Конфигурация

### Claude Desktop - Локальный доступ (stdio)

```json
{
  "mcpServers": {
    "mcp-airflow-api": {
      "command": "uvx",
      "args": ["--python", "3.12", "mcp-airflow-api"],
      "env": {
        "AIRFLOW_API_VERSION": "v2",
        "AIRFLOW_API_BASE_URL": "http://localhost:8080/api",
        "AIRFLOW_API_USERNAME": "airflow",
        "AIRFLOW_API_PASSWORD": "airflow"
      }
    }
  }
}
```

### Claude Desktop - Удаленный доступ (streamable-http)

```json
{
  "mcpServers": {
    "mcp-airflow-api": {
      "type": "streamable-http",
      "url": "http://localhost:8000/mcp"
    }
  }
}
```

### Claude Desktop - Удаленный доступ с Bearer токеном

```json
{
  "mcpServers": {
    "mcp-airflow-api": {
      "type": "streamable-http",
      "url": "http://localhost:8000/mcp",
      "headers": {
        "Authorization": "Bearer your-secure-secret-key-here"
      }
    }
  }
}
```

### Множественные кластеры Airflow

```json
{
  "mcpServers": {
    "airflow-2x-cluster": {
      "command": "uvx",
      "args": ["--python", "3.12", "mcp-airflow-api"],
      "env": {
        "AIRFLOW_API_VERSION": "v1",
        "AIRFLOW_API_BASE_URL": "http://localhost:38080/api",
        "AIRFLOW_API_USERNAME": "airflow",
        "AIRFLOW_API_PASSWORD": "airflow"
      }
    },
    "airflow-3x-cluster": {
      "command": "uvx",
      "args": ["--python", "3.12", "mcp-airflow-api"],
      "env": {
        "AIRFLOW_API_VERSION": "v2",
        "AIRFLOW_API_BASE_URL": "http://localhost:48080/api",
        "AIRFLOW_API_USERNAME": "airflow",
        "AIRFLOW_API_PASSWORD": "airflow"
      }
    }
  }
}
```

## Возможности

- Запросы на естественном языке вместо сложного синтаксиса API
- Поддержка нескольких версий API (Airflow 2.x и 3.0+) с динамическим выбором версии
- Комплексные возможности мониторинга для отслеживания здоровья кластера, статуса DAG и выполнения задач
- 45 инструментов для Airflow 3.0+ (43 общих + 2 для управления активами) и 43 инструмента для Airflow 2.x
- Оптимизация для больших окружений с умной пагинацией и расширенной фильтрацией
- Поддержка режимов транспорта stdio и streamable-http
- Полное покрытие Airflow REST API включая управление DAG, мониторинг задач и конфигурацию
- Аутентификация Bearer токеном для безопасного удаленного доступа
- Полная настройка Docker Compose с интеграцией OpenWebUI

## Переменные окружения

### Обязательные
- `AIRFLOW_API_VERSION` - Выбор версии API - v1 для Airflow 2.x, v2 для Airflow 3.0+
- `AIRFLOW_API_BASE_URL` - Базовый URL для эндпоинта Airflow API
- `AIRFLOW_API_USERNAME` - Имя пользователя для аутентификации Airflow API
- `AIRFLOW_API_PASSWORD` - Пароль для аутентификации Airflow API

### Опциональные
- `MCP_LOG_LEVEL` - Уровень логирования (DEBUG/INFO/WARNING/ERROR/CRITICAL)
- `FASTMCP_TYPE` - Режим транспорта - stdio (по умолчанию) или streamable-http
- `FASTMCP_PORT` - Порт HTTP сервера для режима Docker
- `REMOTE_AUTH_ENABLE` - Включить аутентификацию Bearer токеном для режима streamable-http
- `REMOTE_SECRET_KEY` - Секретный ключ для аутентификации Bearer токеном

## Примеры использования

```
Show me the currently running DAGs
```

```
What DAGs are currently running?
```

```
Show me the failed tasks
```

```
Find DAGs containing ETL
```

## Ресурсы

- [GitHub Repository](https://github.com/call518/MCP-Airflow-API)

## Примечания

Поддерживает как Airflow 2.x (API v1 с 43 инструментами), так и Airflow 3.0+ (API v2 с 45 инструментами, включая управление активами). Единый MCP сервер динамически адаптируется на основе переменной окружения AIRFLOW_API_VERSION. Включает комплексную настройку Docker с интеграцией OpenWebUI и сопутствующими тестовыми кластерами, доступными через проект Airflow-Docker-Compose.