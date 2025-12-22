---
title: Odoo MCP сервер
description: MCP сервер, который позволяет AI-ассистентам взаимодействовать с системами Odoo ERP для доступа к бизнес-данным, поиска записей, создания новых записей, обновления данных и управления инстансами Odoo с помощью естественного языка.
tags:
- CRM
- Database
- Integration
- Productivity
- API
author: ivnvxd
featured: true
---

MCP сервер, который позволяет AI-ассистентам взаимодействовать с системами Odoo ERP для доступа к бизнес-данным, поиска записей, создания новых записей, обновления данных и управления инстансами Odoo с помощью естественного языка.

## Установка

### UVX (Рекомендуется)

```bash
uvx mcp-server-odoo
```

### Pip

```bash
pip install mcp-server-odoo
```

### Pipx

```bash
pipx install mcp-server-odoo
```

### Из исходного кода

```bash
git clone https://github.com/ivnvxd/mcp-server-odoo.git
cd mcp-server-odoo
pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "odoo": {
      "command": "uvx",
      "args": ["mcp-server-odoo"],
      "env": {
        "ODOO_URL": "https://your-odoo-instance.com",
        "ODOO_API_KEY": "your-api-key-here",
        "ODOO_DB": "your-database-name"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "odoo": {
      "command": "uvx",
      "args": ["mcp-server-odoo"],
      "env": {
        "ODOO_URL": "https://your-odoo-instance.com",
        "ODOO_API_KEY": "your-api-key-here",
        "ODOO_DB": "your-database-name"
      }
    }
  }
}
```

### VS Code

```json
{
  "github.copilot.chat.mcpServers": {
    "odoo": {
      "command": "uvx",
      "args": ["mcp-server-odoo"],
      "env": {
        "ODOO_URL": "https://your-odoo-instance.com",
        "ODOO_API_KEY": "your-api-key-here",
        "ODOO_DB": "your-database-name"
      }
    }
  }
}
```

### Zed

```json
{
  "context_servers": {
    "odoo": {
      "command": "uvx",
      "args": ["mcp-server-odoo"],
      "env": {
        "ODOO_URL": "https://your-odoo-instance.com",
        "ODOO_API_KEY": "your-api-key-here",
        "ODOO_DB": "your-database-name"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_records` | Поиск записей в любой модели Odoo с фильтрами |
| `get_record` | Получение конкретной записи по ID |
| `list_models` | Список всех моделей, доступных для MCP |
| `create_record` | Создание новой записи в Odoo |
| `update_record` | Обновление существующей записи |
| `delete_record` | Удаление записи из Odoo |

## Возможности

- Поиск и получение любых записей Odoo (клиенты, товары, счета и т.д.)
- Создание новых записей с валидацией полей и проверкой разрешений
- Обновление существующих данных с умной обработкой полей
- Удаление записей с учетом разрешений на уровне модели
- Просмотр множественных записей и получение форматированных сводок
- Подсчет записей, соответствующих конкретным критериям
- Анализ полей модели для понимания структуры данных
- Безопасный доступ с аутентификацией по API ключу или логину/паролю
- Умная пагинация для больших наборов данных
- Оптимизированный для LLM вывод с иерархическим текстовым форматированием

## Переменные окружения

### Обязательные
- `ODOO_URL` - URL вашего инстанса Odoo

### Опциональные
- `ODOO_API_KEY` - API ключ для аутентификации
- `ODOO_USER` - Имя пользователя (если не используете API ключ)
- `ODOO_PASSWORD` - Пароль (если не используете API ключ)
- `ODOO_DB` - Название базы данных (автоопределяется, если не задано)
- `ODOO_YOLO` - YOLO режим - обходит безопасность MCP (⚠️ ТОЛЬКО ДЛЯ РАЗРАБОТКИ)

## Примеры использования

```
Покажи мне всех клиентов из Испании
```

```
Найди товары с остатками менее 10 единиц
```

```
Покажи сегодняшние заказы на сумму свыше $1000
```

```
Найди неоплаченные счета за прошлый месяц
```

```
Посчитай сколько у нас активных сотрудников
```

## Ресурсы

- [GitHub Repository](https://github.com/ivnvxd/mcp-server-odoo)

## Примечания

Требует Python 3.10+, Odoo 17.0+. Для продакшн использования установите модуль Odoo MCP. YOLO режим доступен для тестирования без установки модуля, но никогда не должен использоваться в продакшне. Поддерживает множественные транспортные протоколы, включая stdio и streamable-http.