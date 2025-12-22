---
title: Kafka MCP сервер
description: Сервер Model Context Protocol (MCP) для Apache Kafka, который позволяет LLM-моделям выполнять основные операции Kafka, такие как отправка/получение сообщений, управление топиками, мониторинг групп потребителей и оценка состояния кластера через стандартизированный интерфейс.
tags:
- Messaging
- Monitoring
- DevOps
- Integration
- Analytics
author: tuannvm
featured: false
install_command: "claude mcp add kafka \\\n  --env KAFKA_BROKERS=localhost:9092 \\\
  \n  --env KAFKA_CLIENT_ID=kafka-mcp-server \\\n  --env MCP_TRANSPORT=stdio \\\n\
  \  --env KAFKA_SASL_MECHANISM= \\\n  --env KAFKA_SASL_USER= \\\n  --env KAFKA_SASL_PASSWORD=\
  \ \\\n  --env KAFKA_TLS_ENABLE=false \\\n  -- kafka-mcp-server"
---

Сервер Model Context Protocol (MCP) для Apache Kafka, который позволяет LLM-моделям выполнять основные операции Kafka, такие как отправка/получение сообщений, управление топиками, мониторинг групп потребителей и оценка состояния кластера через стандартизированный интерфейс.

## Установка

### Homebrew

```bash
# Add the tap repository
brew tap tuannvm/mcp

# Install kafka-mcp-server
brew install kafka-mcp-server
```

### Из исходного кода

```bash
# Clone the repository
git clone https://github.com/tuannvm/kafka-mcp-server.git
cd kafka-mcp-server

# Build the server
go build -o kafka-mcp-server ./cmd
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "kafka": {
      "command": "kafka-mcp-server",
      "args": [],
      "env": {
        "KAFKA_BROKERS": "localhost:9092",
        "KAFKA_CLIENT_ID": "kafka-mcp-server",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "kafka": {
      "command": "kafka-mcp-server",
      "args": [],
      "env": {
        "KAFKA_BROKERS": "localhost:9092",
        "KAFKA_CLIENT_ID": "kafka-mcp-server",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

### ChatWise

```json
Конфигурация:
- **ID**: `kafka`
- **Command**: `kafka-mcp-server`
- **Args**: (оставить пустым)
- **Env**: Добавить переменные окружения:
  ```
  KAFKA_BROKERS=localhost:9092
  KAFKA_CLIENT_ID=kafka-mcp-server
  MCP_TRANSPORT=stdio
  ```
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `produce_message` | Отправляет сообщения в топики Kafka |
| `consume_messages` | Получает сообщения из топиков Kafka в пакетных операциях |
| `list_brokers` | Выводит все настроенные адреса брокеров Kafka |
| `describe_topic` | Предоставляет исчерпывающие метаданные для конкретных топиков |
| `list_consumer_groups` | Перечисляет все группы потребителей в кластере |
| `describe_consumer_group` | Предоставляет детальную информацию о группе потребителей, включая метрики задержки |
| `describe_configs` | Получает настройки конфигурации для ресурсов Kafka |
| `cluster_overview` | Предоставляет исчерпывающую сводку состояния кластера |
| `list_topics` | Выводит все топики с метаданными, включая информацию о партициях и репликации |

## Возможности

- Интеграция с Kafka: Реализация основных операций Kafka через MCP
- Безопасность: Поддержка SASL (PLAIN, SCRAM-SHA-256, SCRAM-SHA-512) и TLS аутентификации
- OAuth 2.1 аутентификация для HTTP транспорта (Native и Proxy режимы)
- Поддержка провайдеров Okta, Google, Azure AD и HMAC
- Гибкий транспорт: STDIO для локальных клиентов, HTTP для удаленного доступа
- Обработка ошибок с понятной обратной связью
- Опции конфигурации: Настраиваемые для разных сред
- Предварительно настроенные промпты: Набор промптов для основных операций Kafka
- Совместимость: Работает с MCP-совместимыми LLM-моделями

## Переменные окружения

### Опциональные
- `KAFKA_BROKERS` - Список адресов брокеров Kafka через запятую
- `KAFKA_CLIENT_ID` - ID клиента Kafka, используемый для подключений
- `MCP_TRANSPORT` - Метод транспорта MCP (stdio/http)
- `KAFKA_SASL_MECHANISM` - SASL механизм: plain, scram-sha-256, scram-sha-512, или "" (отключен)
- `KAFKA_SASL_USER` - Имя пользователя для SASL аутентификации
- `KAFKA_SASL_PASSWORD` - Пароль для SASL аутентификации
- `KAFKA_TLS_ENABLE` - Включить TLS для подключения к Kafka (true или false)
- `KAFKA_TLS_INSECURE_SKIP_VERIFY` - Пропустить проверку TLS сертификатов (true или false)

## Примеры использования

```
Нам нужно выяснить, почему наш pipeline обработки заказов отстает. Можешь помочь мне проверить задержку потребителей?
```

```
Можешь показать мне состояние нашего кластера Kafka?
```

```
Покажи все группы потребителей и их текущий статус задержки
```

```
Какие топики доступны в нашем кластере Kafka?
```

```
Проверь недорепликированные партиции в кластере
```

## Ресурсы

- [GitHub Repository](https://github.com/tuannvm/kafka-mcp-server)

## Примечания

Включает MCP ресурсы (kafka-mcp://overview, kafka-mcp://health-check, и т.д.) и MCP промпты (kafka_cluster_overview, kafka_health_check, и т.д.). Поддерживает инструмент mcpenetes для более простого управления конфигурацией в нескольких MCP клиентах. OAuth 2.1 аутентификация доступна только с HTTP транспортом. Подробная документация доступна для инструментов, ресурсов и промптов в отдельных файлах документации.