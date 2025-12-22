---
title: Eunomia MCP сервер
description: Расширение фреймворка Eunomia, которое соединяет инструменты Eunomia с MCP серверами для управления политиками корпоративного управления данными, такими как обнаружение персональной информации и контроль доступа пользователей в текстовых пайплайнах.
tags:
- Security
- Integration
- AI
- Analytics
author: Community
featured: false
---

Расширение фреймворка Eunomia, которое соединяет инструменты Eunomia с MCP серверами для управления политиками корпоративного управления данными, такими как обнаружение персональной информации и контроль доступа пользователей в текстовых пайплайнах.

## Установка

### Из исходного кода

```bash
git clone https://github.com/whataboutyou-ai/eunomia-mcp-server.git
```

### Запуск сервера

```bash
uv --directory "path/to/server/" run orchestra_server
```

## Конфигурация

### Конфигурация настроек

```json
from pydantic_settings import BaseSettings
from pydantic import ConfigDict
from eunomia.orchestra import Orchestra
from eunomia.instruments import IdbacInstrument, PiiInstrument

class Settings(BaseSettings):
    APP_NAME: str = "mcp-server_orchestra"
    APP_VERSION: str = "0.1.0"
    LOG_LEVEL: str = "info"
    MCP_SERVERS: dict = {
        "web-browser-mcp-server": {
            "command": "uv",
            "args": [
                "tool",
                "run",
                "web-browser-mcp-server"
            ],
            "env": {
                "REQUEST_TIMEOUT": "30"
            }
        }
    }
    ORCHESTRA: Orchestra = Orchestra(
        instruments=[
            PiiInstrument(entities=["EMAIL_ADDRESS", "PERSON"], edit_mode="replace"),
        ]
    )
```

## Возможности

- Обеспечение управления данными поверх LLM или текстовых пайплайнов
- Оркестрация множественных серверов, которые взаимодействуют через MCP фреймворк
- Обнаружение и замена персональной информации с настраиваемыми сущностями
- Интеграция с внешними MCP серверами
- Настраиваемые инструменты для политик управления данными
- Возможности контроля доступа пользователей

## Переменные окружения

### Опциональные
- `REQUEST_TIMEOUT` - Значение таймаута для запросов к MCP серверу

## Ресурсы

- [GitHub Repository](https://github.com/whataboutyou-ai/eunomia-MCP-server)

## Примечания

Этот MCP сервер устарел, поскольку он несовместим с последними разработками Eunomia. Новая интеграция с MCP находится в разработке и будет доступна в ближайшее время. Сервер использует концепцию Orchestra от Eunomia с инструментами для применения политик управления данными к текстовым потокам.