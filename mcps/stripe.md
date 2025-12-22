---
title: Stripe MCP сервер
description: Сервер Model Context Protocol, который интегрируется со Stripe для обработки платежей, работы с клиентами и возвратов, обеспечивая безопасное управление финансовыми транзакциями с ведением журнала аудита.
tags:
- Finance
- API
- Integration
- Security
- Analytics
author: Community
featured: false
install_command: npx -y @smithery/cli install @atharvagupta2003/mcp-stripe --client
  claude
---

Сервер Model Context Protocol, который интегрируется со Stripe для обработки платежей, работы с клиентами и возвратов, обеспечивая безопасное управление финансовыми транзакциями с ведением журнала аудита.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @atharvagupta2003/mcp-stripe --client claude
```

### Из исходного кода

```bash
python -m venv venv
source venv/bin/activate  # На macOS/Linux
venv\Scripts\activate    # На Windows
pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "stripe": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/PARENT/FOLDER/src",
        "run",
        "server.py"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `customer_create` | Создать нового клиента |
| `customer_retrieve` | Получить данные клиента |
| `customer_update` | Обновить информацию о клиенте |
| `payment_intent_create` | Создать платежное намерение для обработки платежей |
| `charge_list` | Показать список последних списаний |
| `refund_create` | Создать возврат для списания |

## Возможности

- Безопасные платежи: интеграция со Stripe для надежной обработки платежей
- Журнал аудита: отслеживание всех транзакций Stripe
- Обработка ошибок: комплексная обработка ошибок с понятными сообщениями
- Интеграция MCP: поддержка MCP-совместимых инструментов и списка ресурсов
- Хранение журналов аудита операций с клиентами, платежами и возвратами
- Поддержка структурированного логирования для лучшей отслеживаемости

## Переменные окружения

### Обязательные
- `STRIPE_API_KEY` - ваш секретный ключ Stripe для аутентификации API

## Примеры использования

```
Создать нового клиента с email customer@example.com и именем John Doe
```

```
Получить данные клиента для ID клиента cus_123456
```

```
Создать платежное намерение на $50.00 в USD для конкретного клиента
```

```
Создать возврат для списания ch_abc123
```

## Ресурсы

- [GitHub Repository](https://github.com/atharvagupta2003/mcp-stripe)

## Примечания

Требует Python 3.8+, MCP SDK 0.1.0+, Stripe Python SDK и dotenv. Обеспечивает комплексную обработку ошибок для распространенных сценариев, таких как отсутствующие API ключи, некорректные ID клиентов и неправильные параметры. Включает поддержку тестирования MCP Inspector.