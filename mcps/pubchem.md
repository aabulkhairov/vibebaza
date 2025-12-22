---
title: PubChem MCP сервер
description: MCP сервер для извлечения базовой химической информации о лекарствах из PubChem API, предоставляющий комплексные молекулярные данные включая формулы, веса и химические идентификаторы.
tags:
- API
- Database
- Search
- Analytics
author: Community
featured: false
---

MCP сервер для извлечения базовой химической информации о лекарствах из PubChem API, предоставляющий комплексные молекулярные данные включая формулы, веса и химические идентификаторы.

## Установка

### Из исходного кода

```bash
git clone [project repository URL]
cd [project directory]
pip install .
```

### UVX

```bash
uvx pubchem_mcp_server
```

## Конфигурация

### servers_config.json

```json
{
  "mcpServers": {
    "pubchem": {
      "command": "uvx",
      "args": ["pubchem_mcp_server"]
    }
  }
}
```

## Возможности

- Извлечение базовой химической информации о лекарствах из PubChem API
- Получение CAS номеров и молекулярных весов
- Получение молекулярных формул и SMILES нотации
- Получение синонимов лекарств и альтернативных названий
- Доступ к InChI ключам и IUPAC названиям
- Получение ATC кодов для классификации лекарств
- Предоставление прямых ссылок на страницы соединений PubChem

## Ресурсы

- [GitHub Repository](https://github.com/sssjiang/pubchem_mcp_server)

## Примечания

Требует Python 3.10 и зависимости: python-dotenv, requests, mcp, uvicorn. Пример вывода показывает комплексную информацию о лекарстве для аспирина, включая молекулярные данные и синонимы.