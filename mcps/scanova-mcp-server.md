---
title: Scanova MCP сервер
description: MCP сервер для создания и управления QR-кодами через Scanova API, предоставляющий инструменты для создания, управления и скачивания QR-кодов в MCP-совместимых IDE.
tags:
- API
- Productivity
- Integration
- Media
author: trycon
featured: false
---

MCP сервер для создания и управления QR-кодами через Scanova API, предоставляющий инструменты для создания, управления и скачивания QR-кодов в MCP-совместимых IDE.

## Установка

### Локальная разработка

```bash
git clone <repository-url>
cd qcg-mcp
uv sync
uv run cloud_server.py
```

### Docker

```bash
docker build -t mcpserver:local .
docker run -d --name mcpserver -p 8000:8000 mcpserver:local
```

### Docker Compose

```bash
docker compose up -d
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "scanova-mcp": {
      "transport": "http",
      "url": "https://mcp.scanova.io/mcp",
      "headers": {
        "Authorization": "YOUR_SCANOVA_API_KEY_HERE"
      }
    }
  }
}
```

### VS Code

```json
{
  "mcpServers": {
    "scanova-mcp": {
      "transport": "http", 
      "url": "https://mcp.scanova.io/mcp",
      "headers": {
        "Authorization": "YOUR_SCANOVA_API_KEY_HERE"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "scanova-mcp": {
      "transport": "http",
      "url": "https://mcp.scanova.io/mcp", 
      "headers": {
        "Authorization": "YOUR_SCANOVA_API_KEY_HERE"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `create_qr_code` | Создать новый QR-код |
| `list_qr_codes` | Показать существующие QR-коды |
| `update_qr_code` | Обновить существующий QR-код |
| `retrieve_qr_code` | Получить детали QR-кода |
| `download_qr_code` | Скачать изображение QR-кода |
| `activate_qr_code` | Активировать QR-код |
| `deactivate_qr_code` | Деактивировать QR-код |

## Возможности

- Создание QR-кодов: Генерация динамических QR-кодов с пользовательскими URL
- Список QR-кодов: Просмотр всех существующих QR-кодов с пагинацией
- Обновление QR-кодов: Изменение существующих QR-кодов с новыми URL или именами
- Получение деталей QR-кода: Подробная информация о конкретных QR-кодах
- Скачивание QR-кодов: Загрузка изображений QR-кодов в различных форматах
- Активация/деактивация QR-кодов: Управление статусом QR-кодов

## Примеры использования

```
create qr
```

```
make qr code
```

```
generate qr
```

```
list qr codes
```

```
show qr codes
```

## Ресурсы

- [GitHub Repository](https://github.com/trycon/scanova-mcp)

## Примечания

Требуется API ключ Scanova с https://app.scanova.io/. Сервер размещен по адресу https://mcp.scanova.io/mcp и предоставляет эндпоинты для проверки здоровья и информации о сервисе. Лицензия MIT.