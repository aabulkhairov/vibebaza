---
title: kafka-mcp сервер
description: MCP сервер, который предоставляет интерфейс на естественном языке для управления операциями Kafka, позволяя AI агентам взаимодействовать с кластерами Kafka для публикации и потребления сообщений, а также управления топиками, брокерами и партициями.
tags:
- Messaging
- DevOps
- Integration
- Analytics
author: shivamxtech
featured: false
---

MCP сервер, который предоставляет интерфейс на естественном языке для управления операциями Kafka, позволяя AI агентам взаимодействовать с кластерами Kafka для публикации и потребления сообщений, а также управления топиками, брокерами и партициями.

## Установка

### Из исходного кода

```bash
python3 -m venv .venv
source .venv/bin/activate  # On macOS/Linux
.venv\Scripts\activate     # On Windows
pip install -r requirements.txt
# Or using uv
uv pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "kafka-mcp": {
      "command": "python3",
      "args": ["/Users/I528600/Desktop/mcp/kafka-mcp/src/main.py"],
      "env": {
        "BOOTSTRAP_SERVERS": "localhost:9092",
        "MCP_TRANSPORT": "stdio"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `consumer` | Потребление сообщений из топиков Kafka |
| `producer` | Публикация сообщений в топики Kafka |
| `topic` | Список, создание, удаление и описание топиков в Kafka |
| `broker` | Получение информации о брокере |
| `partition` | Получение партиций и смещений партиций |
| `group_offset` | Получение и сброс смещений в Kafka |

## Возможности

- Запросы на естественном языке: Позволяет AI агентам запрашивать и обновлять Kafka, используя естественный язык
- Бесшовная интеграция с MCP: Работает с любым MCP клиентом для плавной коммуникации
- Полная поддержка Kafka: Обрабатывает продюсеры, консьюмеры, топики, брокеры, партиции и смещения
- Масштабируемость и легковесность: Разработан для высокопроизводительных операций с данными

## Переменные окружения

### Обязательные
- `BOOTSTRAP_SERVERS` - URL вашего сервера Kafka
- `MCP_TRANSPORT` - Транспортный протокол для MCP коммуникации

## Примеры использования

```
Publish message 'i am using kafka server' on the topic 'test-kafka'
```

```
Consume the message from topic 'test-kafka'
```

```
List all topics from the kafka environment
```

```
List all topics in the kafka cluster
```

```
Create topic 'my-kafka' in kafka cluster
```

## Ресурсы

- [GitHub Repository](https://github.com/shivamxtech/kafka-mcp)

## Примечания

Запускайте сервер с помощью 'python3 src/main.py' или 'uv run python3 src/main.py'. Сервер требует запущенного кластера Kafka и правильной конфигурации bootstrap серверов.