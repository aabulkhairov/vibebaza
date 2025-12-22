---
title: Wikifunctions MCP сервер
description: MCP сервер, который позволяет AI моделям находить и выполнять функции из библиотеки WikiFunctions — проекта Wikimedia для создания, курирования и совместного использования кода.
tags:
- Code
- API
- Integration
- Search
- Productivity
author: Fredibau
featured: false
---

MCP сервер, который позволяет AI моделям находить и выполнять функции из библиотеки WikiFunctions — проекта Wikimedia для создания, курирования и совместного использования кода.

## Установка

### NPX

```bash
npx -y fredibau-wikifunctions-mcp
```

## Конфигурация

### MCP-совместимые инструменты (Claude Desktop, Cursor)

```json
{
  "mcpServers": {
    "wikifunctions": {
      "command": "npx",
      "args": ["-y", "fredibau-wikifunctions-mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `find_code` | Ищет функцию в WikiFunctions и возвращает исходный код её реализации для изучения... |
| `get_template` | Получает определение функции WikiFunctions и создаёт JSON шаблон для её вызова, включ... |
| `run_template` | Выполняет вызов функции в WikiFunctions используя предоставленный шаблон и значения аргументов, преобраз... |

## Возможности

- Поиск функций в WikiFunctions и получение исходного кода
- Создание JSON шаблонов для вызова функций с информацией о типах
- Выполнение WikiFunctions с пользовательскими аргументами
- Взаимодействие с API эндпоинтами WikiFunctions
- Преобразование type ZID в человеко-читаемые имена
- Трансформация удобных для пользователя шаблонов в валидные объекты вызова функций WikiFunctions

## Ресурсы

- [GitHub Repository](https://github.com/Fredibau/wikifunctions-mcp-fredibau)

## Примечания

Сервер взаимодействует с несколькими API эндпоинтами WikiFunctions, включая wikilambdasearch_functions для поиска функций, wikilambda_fetch для получения детальной информации и wikifunctions_run для выполнения функций.