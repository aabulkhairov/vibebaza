---
title: AWS Cost Explorer MCP сервер
description: MCP сервер для анализа данных о расходах AWS через Cost Explorer и статистики использования Amazon Bedrock через логи вызовов моделей в Amazon CloudWatch, позволяющий делать запросы о паттернах трат AWS на естественном языке.
tags:
- Cloud
- Analytics
- Finance
- Monitoring
- DevOps
author: aarora79
featured: true
---

MCP сервер для анализа данных о расходах AWS через Cost Explorer и статистики использования Amazon Bedrock через логи вызовов моделей в Amazon CloudWatch, позволяющий делать запросы о паттернах трат AWS на естественном языке.

## Установка

### Из исходников с UV

```bash
git clone https://github.com/aarora79/aws-cost-explorer-mcp.git
cd aws-cost-explorer-mcp
uv venv --python 3.12 && source .venv/bin/activate && uv pip install --requirement pyproject.toml
```

### Docker

```bash
docker build -t aws-cost-explorer-mcp .
docker run -v ~/.aws:/root/.aws aws-cost-explorer-mcp
```

### Локальный сервер

```bash
export MCP_TRANSPORT=stdio
export BEDROCK_LOG_GROUP_NAME=YOUR_BEDROCK_CW_LOG_GROUP_NAME
export CROSS_ACCOUNT_ROLE_NAME=ROLE_NAME_FOR_THE_ROLE_TO_ASSUME_IN_OTHER_ACCOUNTS
python server.py
```

## Конфигурация

### Claude Desktop - Docker

```json
{
  "mcpServers": {
    "aws-cost-explorer": {
      "command": "docker",
      "args": [ "run", "-i", "--rm", "-e", "AWS_ACCESS_KEY_ID", "-e", "AWS_SECRET_ACCESS_KEY", "-e", "AWS_REGION", "-e", "BEDROCK_LOG_GROUP_NAME", "-e", "MCP_TRANSPORT", "-e", "CROSS_ACCOUNT_ROLE_NAME", "aws-cost-explorer-mcp:latest" ],
      "env": {
        "AWS_ACCESS_KEY_ID": "YOUR_ACCESS_KEY_ID",
        "AWS_SECRET_ACCESS_KEY": "YOUR_SECRET_ACCESS_KEY",
        "AWS_REGION": "us-east-1",
        "BEDROCK_LOG_GROUP_NAME": "YOUR_CLOUDWATCH_BEDROCK_MODEL_INVOCATION_LOG_GROUP_NAME",
        "CROSS_ACCOUNT_ROLE_NAME": "ROLE_NAME_FOR_THE_ROLE_TO_ASSUME_IN_OTHER_ACCOUNTS",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

### Claude Desktop - UV

```json
{
  "mcpServers": {
    "aws_cost_explorer": {
      "command": "uv",
      "args": [
          "--directory",
          "/path/to/aws-cost-explorer-mcp-server",
          "run",
          "server.py"
      ],
      "env": {
        "AWS_ACCESS_KEY_ID": "YOUR_ACCESS_KEY_ID",
        "AWS_SECRET_ACCESS_KEY": "YOUR_SECRET_ACCESS_KEY",
        "AWS_REGION": "us-east-1",
        "BEDROCK_LOG_GROUP_NAME": "YOUR_CLOUDWATCH_BEDROCK_MODEL_INVOCATION_LOG_GROUP_NAME",
        "CROSS_ACCOUNT_ROLE_NAME": "ROLE_NAME_FOR_THE_ROLE_TO_ASSUME_IN_OTHER_ACCOUNTS",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_ec2_spend_last_day` | Получает данные о расходах на EC2 за предыдущий день |
| `get_detailed_breakdown_by_day` | Предоставляет комплексный анализ затрат по регионам, сервисам и типам инстансов |
| `get_bedrock_daily_usage_stats` | Предоставляет ежедневную статистику использования моделей по регионам и пользователям |
| `get_bedrock_hourly_usage_stats` | Предоставляет почасовую статистику использования моделей по регионам и пользователям |

## Возможности

- Анализ расходов Amazon EC2: Просмотр детализированной разбивки трат на EC2 за последний день
- Анализ расходов Amazon Bedrock: Просмотр разбивки по регионам, пользователям и моделям за последние 30 дней
- Отчеты по тратам на сервисы: Анализ расходов по всем сервисам AWS за последние 30 дней
- Детальная разбивка затрат: Получение гранулярных данных о затратах по дням, регионам, сервисам и типам инстансов
- Интерактивный интерфейс: Использование Claude для запросов к данным о затратах на естественном языке
- Межаккаунтный доступ: Получение информации о тратах AWS из других аккаунтов с правильным принятием IAM ролей
- Поддержка удаленного MCP сервера: Запуск сервера на Amazon EC2 с поддержкой HTTPS через nginx reverse proxy
- Интеграция с LangGraph Agent: Использование с Chainlit приложением для интерфейса чат-бота

## Переменные окружения

### Обязательные
- `MCP_TRANSPORT` - Метод транспорта для MCP (stdio для локального, sse для удаленного)
- `BEDROCK_LOG_GROUP_NAME` - Название группы логов CloudWatch для логов вызовов моделей Bedrock
- `AWS_ACCESS_KEY_ID` - ID ключа доступа AWS для аутентификации
- `AWS_SECRET_ACCESS_KEY` - Секретный ключ доступа AWS для аутентификации
- `AWS_REGION` - Регион AWS для использования

### Опциональные
- `CROSS_ACCOUNT_ROLE_NAME` - Название роли для принятия ролей в других AWS аккаунтах для получения информации о межаккаунтных тратах

## Примеры использования

```
Помоги мне понять мои расходы на Bedrock за последние несколько недель
```

```
Сколько я потратил на EC2 вчера?
```

```
Покажи мне топ-5 AWS сервисов по затратам за последний месяц
```

```
Проанализируй мои траты по регионам за последние 14 дней
```

```
Какие типы инстансов обходятся мне дороже всего?
```

## Ресурсы

- [GitHub Repository](https://github.com/aarora79/aws-cost-explorer-mcp-server)

## Примечания

Требуются AWS credentials с доступом к Cost Explorer и соответствующие разрешения IAM для CloudWatch Logs. Для отслеживания использования Bedrock необходимо настроить логи вызовов моделей в Amazon CloudWatch. Поддерживает как локальное, так и удаленное развертывание с поддержкой HTTPS через nginx reverse proxy. Обратите внимание, что Claude Desktop в настоящее время не поддерживает удаленные MCP серверы.