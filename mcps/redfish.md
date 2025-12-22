---
title: Redfish MCP сервер
description: Интерфейс на естественном языке для AI агентов, позволяющий управлять инфраструктурой через DMTF Redfish API, включая запросы о серверах, сетевых интерфейсах и других компонентах инфраструктуры.
tags:
- DevOps
- API
- Monitoring
- Cloud
- Integration
author: nokia
featured: false
---

Интерфейс на естественном языке для AI агентов, позволяющий управлять инфраструктурой через DMTF Redfish API, включая запросы о серверах, сетевых интерфейсах и других компонентах инфраструктуры.

## Установка

### Из исходного кода

```bash
git clone <repository-url>
cd mcp-redfish
make install
uv run mcp-redfish
```

### Настройка для разработки

```bash
git clone <repository-url>
cd mcp-redfish
make dev
uv run mcp-redfish
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "redfish": {
            "command": "<full_path_uv_command>",
            "args": [
                "--directory",
                "<your_mcp_server_directory>",
                "run",
                "mcp-redfish"
            ],
            "env": {
                "REDFISH_HOSTS": "[{\"address\": \"192.168.1.100\", \"username\": \"admin\", \"password\": \"secret123\"}]",
                "REDFISH_AUTH_METHOD": "session",
                "MCP_TRANSPORT": "stdio",
                "MCP_REDFISH_LOG_LEVEL": "INFO"
            }
        }
    }
}
```

### VS Code

```json
{
  "mcp": {
    "servers": {
      "redfish": {
        "type": "stdio",
        "command": "<full_path_uv_command>",
        "args": [
          "--directory",
          "<your_mcp_server_directory>",
          "run",
          "mcp-redfish"
        ],
        "env": {
          "REDFISH_HOSTS": "[{\"address\": \"192.168.1.100\", \"username\": \"admin\", \"password\": \"secret123\"}]",
          "REDFISH_AUTH_METHOD": "session",
          "MCP_TRANSPORT": "stdio"
        }
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_endpoints` | Запрос конечных точек Redfish API, настроенных для MCP сервера |
| `get_resource_data` | Чтение данных конкретного ресурса (например, System, EthernetInterface и т.д.) |

## Возможности

- Запросы на естественном языке: позволяет AI агентам запрашивать данные компонентов инфраструктуры на естественном языке
- Бесшовная интеграция с MCP: работает с любым MCP клиентом для плавного взаимодействия
- Полная поддержка Redfish: обёртка для Python библиотеки Redfish
- Несколько транспортных механизмов (stdio, SSE, streamable-http)
- Комплексная валидация конфигурации
- Поддержка SSL/TLS с пользовательскими сертификатами CA
- Автоматическое обнаружение конечных точек
- Поддержка базовой аутентификации и аутентификации по сессии

## Переменные окружения

### Обязательные
- `REDFISH_HOSTS` - JSON массив конфигураций конечных точек Redfish

### Опциональные
- `REDFISH_PORT` - Порт по умолчанию для Redfish API (используется, когда не указан для конкретного хоста)
- `REDFISH_AUTH_METHOD` - Метод аутентификации: basic или session
- `REDFISH_USERNAME` - Имя пользователя по умолчанию для аутентификации
- `REDFISH_PASSWORD` - Пароль по умолчанию для аутентификации
- `REDFISH_SERVER_CA_CERT` - Путь к сертификату CA для проверки сервера
- `REDFISH_DISCOVERY_ENABLED` - Включить автоматическое обнаружение конечных точек
- `REDFISH_DISCOVERY_INTERVAL` - Интервал обнаружения в секундах
- `MCP_TRANSPORT` - Метод транспорта: stdio, sse или streamable-http

## Примеры использования

```
Покажи доступные компоненты инфраструктуры
```

```
Получи данные ethernet интерфейсов компонента инфраструктуры X
```

## Ресурсы

- [Репозиторий на GitHub](https://github.com/nokia/mcp-redfish)

## Примечания

Поддерживает несколько сред выполнения контейнеров (Docker/Podman), включает комплексное end-to-end тестирование с DMTF Redfish Interface Emulator и предоставляет обширный инструментарий для разработки с более чем 42 целями Makefile. Репозиторий: https://github.com/nokia/mcp-redfish