---
title: VolcEngine TOS MCP сервер
description: Официальный MCP сервер от TOS предоставляет мощные возможности запросов, позволяя удобно исследовать и находить контент, хранящийся в VolcEngine TOS, используя естественный язык. Это повышает интуитивность и эффективность доступа к данным.
tags:
- Storage
- Cloud
- Search
- API
- Productivity
author: Community
featured: false
---

Официальный MCP сервер от TOS предоставляет мощные возможности запросов, позволяя удобно исследовать и находить контент, хранящийся в VolcEngine TOS, используя естественный язык. Это повышает интуитивность и эффективность доступа к данным.

## Установка

### UV Build

```bash
uv sync
uv build
```

### UVX

```bash
uvx --from git+https://github.com/volcengine/mcp-server#subdirectory=server/mcp_server_tos mcp-server-tos
```

## Конфигурация

### Локальная конфигурация

```json
{
  "mcpServers": {
    "tos-mcp-server": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/PARENT/FOLDER/src/mcp_server_tos",
        "run",
        "mcp-server-tos"
      ]
    }
  }
}
```

### UVX конфигурация

```json
{
  "mcpServers": {
    "tos-mcp": {
      "command": "uvx",
      "args": [
        "--from",
        "git+https://github.com/volcengine/mcp-server#subdirectory=server/mcp_server_tos",
        "mcp-server-tos"
      ],
      "env": {
        "VOLCENGINE_ACCESS_KEY": "your access-key-id",
        "VOLCENGINE_SECRET_KEY": "your access-key-secret",
        "VOLCENGINE_REGION": "tos region",
        "TOS_ENDPOINT": "tos endpoint",
        "SECURITY_TOKEN": "your security token",
        "TOS_BUCKET": "your specific bucket"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_buckets` | Запрашивает список всех бакетов хранения в вашем аккаунте, возвращает имя бакета, время создания, информацию о местоположении, домен доступа и другую информацию |
| `list_objects` | Запрашивает список объектов указанного бакета хранения, каждый запрос возвращает часть или все объекты в бакете (максимум 1000) |
| `get_object` | Получает содержимое указанного объекта, для текстовых файлов возвращает их содержимое, для изображений, видео и других бинарных объектов возвращает содержимое в формате Base64 |

## Возможности

- Удобное исследование и поиск контента, хранящегося в TOS, используя естественный язык
- Поддержка просмотра списка бакетов хранения VolcEngine TOS
- Поддержка перечисления объектов в бакете (максимум 1000)
- Поддержка получения содержимого текстовых и бинарных объектов
- Может использоваться в комбинации с MCP облачных продуктов VolcEngine
- Поддержка пагинации при перечислении объектов
- Совместимость с платформами Ark, Python, Cursor

## Переменные окружения

### Обязательные
- `VOLCENGINE_ACCESS_KEY` - ACCESS KEY аккаунта VolcEngine
- `VOLCENGINE_SECRET_KEY` - SECRET KEY аккаунта VolcEngine
- `VOLCENGINE_REGION` - регион VolcEngine TOS
- `TOS_ENDPOINT` - Endpoint VolcEngine TOS

### Опциональные
- `SECURITY_TOKEN` - Security Token VolcEngine, опционально
- `TOS_BUCKETS` - указывает TOS бакеты для доступа, опционально

## Примеры использования

```
Перечислить список бакетов хранения VolcEngine TOS
```

```
Перечислить объекты в бакете example VolcEngine TOS
```

```
Прочитать содержимое файла с именем example.txt в бакете example VolcEngine TOS
```

## Ресурсы

- [GitHub Repository](https://github.com/dinghuazhou/sample-mcp-server-tos)

## Примечания

Требуется Python 3.10 или выше, необходимо установить uv. Ссылка для подключения сервиса: https://console.volcengine.com/tos. Используется лицензия MIT.