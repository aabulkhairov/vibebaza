---
title: mcp-sanctions MCP сервер
description: Комплексный MCP сервер для проверки санкций, который использует OFAC API
  для скрининга физических лиц и организаций по основным глобальным санкционным спискам, включая
  OFAC SDN, UN, OFSI и другие.
tags:
- Security
- API
- Finance
- Analytics
author: madupay
featured: false
---

Комплексный MCP сервер для проверки санкций, который использует OFAC API для скрининга физических лиц и организаций по основным глобальным санкционным спискам, включая OFAC SDN, UN, OFSI и другие.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yourusername/mcp-ofac
cd mcp-ofac
npm install
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "sanctions": {
      "command": "/path/to/your/node",
      "args": ["/path/to/your/mcp-ofac/index.js"],
      "env": {
        "OFAC_API_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

## Возможности

- Проверка физических лиц и организаций по основным глобальным санкционным спискам, включая OFAC SDN, UN, OFSI и другие
- Настраиваемый порог риска с минимальными показателями риска для определения релевантности совпадений
- Комплексная поддержка субъектов как для физических лиц, так и для организаций с подробной информацией
- Множественные методы идентификации, включая имена, адреса, документы удостоверяющие личность
- Выбор источников для определения, по каким санкционным спискам проводить проверку в соответствии с требованиями комплаенса

## Переменные окружения

### Обязательные
- `OFAC_API_API_KEY` - API ключ для доступа к сервисам OFAC API

## Примеры использования

```
Can you check if John Smith born on 1980-01-15 from Syria is on any sanctions lists?
```

```
Is there a sanctioned entity called Tech Solutions Ltd based in Tehran, Iran?
```

```
Check if Maria Rodriguez with passport number AB123456 from Venezuela is on the OFAC SDN list with a minimum match score of 90.
```

## Ресурсы

- [GitHub Repository](https://github.com/madupay/mcp-sanctions)

## Примечания

Требует Node.js версии 20 или выше. Сервер обрабатывает запросы на скрининг с настраиваемыми параметрами, включая тип субъекта, минимальный порог оценки (0-100, по умолчанию: 95) и конкретные санкционные списки для проверки. Возвращает подробную информацию о совпадениях, включая данные о санкционированных субъектах, оценки совпадений и информацию об источниках.