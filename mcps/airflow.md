---
title: Airflow MCP сервер
description: Model Context Protocol сервер-обёртка над REST API Apache Airflow. Позволяет
  MCP клиентам взаимодействовать с Airflow стандартизированным способом для управления
  DAG, runs, tasks и многим другим.
tags:
- DevOps
- Monitoring
- Integration
- Analytics
- API
author: yangkyeongmo
featured: true
---

Model Context Protocol сервер-обёртка над REST API Apache Airflow. Позволяет MCP клиентам взаимодействовать с Airflow стандартизированным способом для управления DAG, runs, tasks и многим другим.

## Установка

### UVX

```bash
uvx mcp-server-apache-airflow
```

## Конфигурация

### Claude Desktop — Basic Auth

```json
{
  "mcpServers": {
    "mcp-server-apache-airflow": {
      "command": "uvx",
      "args": ["mcp-server-apache-airflow"],
      "env": {
        "AIRFLOW_HOST": "https://your-airflow-host",
        "AIRFLOW_USERNAME": "your-username",
        "AIRFLOW_PASSWORD": "your-password"
      }
    }
  }
}
```

### Claude Desktop — JWT Token

```json
{
  "mcpServers": {
    "mcp-server-apache-airflow": {
      "command": "uvx",
      "args": ["mcp-server-apache-airflow"],
      "env": {
        "AIRFLOW_HOST": "https://your-airflow-host",
        "AIRFLOW_JWT_TOKEN": "your-jwt-token"
      }
    }
  }
}
```

## Возможности

- Управление DAG — список, детали, пауза/возобновление, обновление, удаление DAG
- DAG Runs — создание, список, обновление, удаление и очистка DAG runs
- Управление задачами — список задач, получение task instances, просмотр логов, очистка и обновление состояний задач
- Переменные — создание, чтение, обновление, удаление переменных Airflow
- Подключения — управление подключениями Airflow и проверка связности
- Пулы — управление ресурсными пулами
- XComs — доступ к данным cross-communication между задачами
- Datasets — управление datasets и dataset events
- Мониторинг — health checks и статистика системы
- Конфигурация — доступ к конфигурации Airflow и плагинам

## Переменные окружения

### Опциональные
- `AIRFLOW_HOST` — URL хоста Airflow
- `AIRFLOW_API_VERSION` — версия API
- `READ_ONLY` — включить read-only режим для безопасности
- `AIRFLOW_USERNAME` — имя пользователя для basic аутентификации
- `AIRFLOW_PASSWORD` — пароль для basic аутентификации
- `AIRFLOW_JWT_TOKEN` — JWT токен для аутентификации (приоритет над basic auth)

## Ресурсы

- [GitHub Repository](https://github.com/yangkyeongmo/mcp-server-apache-airflow)

## Примечания

Использует официальную клиентскую библиотеку Apache Airflow для совместимости. Поддерживает basic аутентификацию и JWT токен аутентификацию. JWT токен имеет приоритет, если указаны оба. Read-only режим рекомендуется для безопасности.
