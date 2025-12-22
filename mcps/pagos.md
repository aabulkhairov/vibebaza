---
title: Pagos MCP сервер
description: MCP сервер, предоставляющий доступ к Pagos API для получения данных по BIN (Bank Identification Number) кредитных карт с базовыми и расширенными опциями данных.
tags:
- API
- Finance
- Analytics
author: pagos-ai
featured: false
---

MCP сервер, предоставляющий доступ к Pagos API для получения данных по BIN (Bank Identification Number) кредитных карт с базовыми и расширенными опциями данных.

## Установка

### Из исходного кода

```bash
brew install uv
git clone https://github.com/pagos-ai/pagos-mcp.git
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "bin-data": {
            "command": "uv",
            "args": [
                "--directory",
                "</path/to/pagos-mcp-server>",
                "run",
                "pagos-mcp-server.py"
            ],
            "env": {
                "PAGOS_API_KEY": "<your-pagos-api-key>",
                "ENHANCED_BIN_DATA": "true"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_bin_data` | Получение BIN данных для указанного BIN номера |

## Возможности

- Получение BIN данных для указанного BIN номера
- Поддержка расширенных атрибутов BIN ответа с более детальной аналитикой
- Базовые BIN запросы с опциональными расширенными функциями

## Переменные окружения

### Обязательные
- `PAGOS_API_KEY` - API ключ для доступа к сервисам Pagos API

### Опциональные
- `ENHANCED_BIN_DATA` - Установите 'true' для расширенных атрибутов BIN ответа, 'false' для базовых данных. По умолчанию 'false'

## Ресурсы

- [GitHub Repository](https://github.com/pagos-ai/pagos-mcp)

## Примечания

Проверьте ваш контракт на предмет дополнительных расходов, связанных с запросами расширенных BIN данных, прежде чем устанавливать ENHANCED_BIN_DATA в 'true'. Следуйте документации Pagos API для генерации API ключа.