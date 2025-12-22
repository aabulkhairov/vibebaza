---
title: InfluxDB MCP сервер
description: MCP сервер, который предоставляет доступ к экземплярам InfluxDB через InfluxDB OSS API v2, позволяя выполнять запросы временных рядов, записывать данные и управлять базами данных.
tags:
- Database
- Analytics
- Monitoring
- DevOps
- API
author: idoru
featured: false
install_command: npx -y @smithery/cli install @idoru/influxdb-mcp-server --client
  claude
---

MCP сервер, который предоставляет доступ к экземплярам InfluxDB через InfluxDB OSS API v2, позволяя выполнять запросы временных рядов, записывать данные и управлять базами данных.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @idoru/influxdb-mcp-server --client claude
```

### NPX

```bash
INFLUXDB_TOKEN=your_token npx influxdb-mcp-server
```

### Глобальная установка

```bash
npm install -g influxdb-mcp-server
INFLUXDB_TOKEN=your_token influxdb-mcp-server
```

### Из исходников

```bash
git clone https://github.com/idoru/influxdb-mcp-server.git
cd influxdb-mcp-server
npm install
INFLUXDB_TOKEN=your_token npm start
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "influxdb": {
      "command": "npx",
      "args": ["influxdb-mcp-server"],
      "env": {
        "INFLUXDB_TOKEN": "your_token",
        "INFLUXDB_URL": "http://localhost:8086",
        "INFLUXDB_ORG": "your_org"
      }
    }
  }
}
```

### Claude Desktop (локально)

```json
{
  "mcpServers": {
    "influxdb": {
      "command": "node",
      "args": ["/path/to/influxdb-mcp-server/src/index.js"],
      "env": {
        "INFLUXDB_TOKEN": "your_token",
        "INFLUXDB_URL": "http://localhost:8086",
        "INFLUXDB_ORG": "your_org"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `write-data` | Записывает данные временных рядов в формате line protocol |
| `query-data` | Выполняет Flux запросы |
| `create-bucket` | Создает новый bucket |
| `create-org` | Создает новую организацию |

## Возможности

- Доступ к данным организаций, bucket'ов и измерений через ресурсы
- Запись данных, выполнение запросов и управление объектами базы данных с помощью инструментов
- Шаблоны для распространенных Flux запросов и формата Line Protocol
- Поддержка транспортных режимов stdio и HTTP
- Комплексный доступ к ресурсам, включая организации, bucket'ы и измерения
- Выполнение запросов с возвратом результатов в качестве ресурсов

## Переменные окружения

### Обязательные
- `INFLUXDB_TOKEN` - Токен аутентификации для InfluxDB API

### Опциональные
- `INFLUXDB_URL` - URL экземпляра InfluxDB
- `INFLUXDB_ORG` - Название организации по умолчанию для некоторых операций

## Ресурсы

- [GitHub Repository](https://github.com/idoru/influxdb-mcp-server)

## Примечания

Сервер поддерживает транспортные режимы stdio (по умолчанию) и HTTP. Может быть запущен с флагом --http для режима Express.js сервера на порту 3000 или кастомном порту. Включает комплексные интеграционные тесты с настройкой Docker контейнера и примерами данных.