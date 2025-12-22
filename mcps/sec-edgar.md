---
title: SEC EDGAR MCP сервер
description: MCP сервер, который подключает AI модели к документам SEC EDGAR для доступа к официальным корпоративным финансовым данным, отчетам и информации об инсайдерской торговле с точной привязкой к документам.
tags:
- Finance
- Database
- API
- Analytics
- Integration
author: stefanoamorelli
featured: true
---

MCP сервер, который подключает AI модели к документам SEC EDGAR для доступа к официальным корпоративным финансовым данным, отчетам и информации об инсайдерской торговле с точной привязкой к документам.

## Установка

### Docker

```bash
docker run -i --rm -e "SEC_EDGAR_USER_AGENT=Your Name (name@domain.com)" stefanoamorelli/sec-edgar-mcp:latest
```

## Конфигурация

### Конфигурация Docker

```json
{
  "mcpServers": {
    "sec-edgar-mcp": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "SEC_EDGAR_USER_AGENT=Your Name (name@domain.com)",
        "stefanoamorelli/sec-edgar-mcp:latest"
      ],
      "env": {}
    }
  }
}
```

## Возможности

- Инструменты компаний: поиск CIK, информация о компании и факты о компании
- Инструменты документов: последние отчеты, содержимое документов, анализ 8-K и извлечение разделов
- Финансовые инструменты: финансовые отчеты с прямым парсингом XBRL для точной привязки
- Инструменты инсайдерской торговли: анализ форм 3/4/5 с детальными данными транзакций
- Детерминированные ответы для предотвращения галлюцинаций AI
- Точная числовая привязка согласно данным, поданным в SEC
- Ссылки на документы с кликабельными SEC URL для верификации
- Гибкое извлечение XBRL с использованием поиска по паттернам

## Переменные окружения

### Обязательные
- `SEC_EDGAR_USER_AGENT` - Обязательная строка user agent для доступа к SEC EDGAR API (формат: Your Name (email@domain.com))

## Примеры использования

```
What's the latest 10-K filing for Apple?
```

```
Show me Tesla's exact revenue from their latest 10-K
```

## Ресурсы

- [GitHub Repository](https://github.com/stefanoamorelli/sec-edgar-mcp)

## Примечания

Поддерживает потоковый HTTP транспорт для платформ типа Dify через аргумент --transport streamable-http. Хост по умолчанию 0.0.0.0, порт 9870. Аутентификация не предусмотрена - используйте только в приватных сетях. Полная документация доступна по адресу https://sec-edgar-mcp.amorelli.tech/