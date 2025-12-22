---
title: Wikidata MCP сервер
description: MCP сервер, который предоставляет инструменты для взаимодействия с
  Wikidata, включая поиск идентификаторов, извлечение метаданных и выполнение SPARQL
  запросов.
tags:
- Database
- Search
- API
- Analytics
author: Community
featured: false
---

MCP сервер, который предоставляет инструменты для взаимодействия с Wikidata, включая поиск идентификаторов, извлечение метаданных и выполнение SPARQL запросов.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @zzaebok/mcp-wikidata --client claude
```

### Из исходников

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
git clone https://github.com/zzaebok/mcp-wikidata.git
cd mcp-wikidata
uv sync
# если хотите запустить клиентский пример
uv sync --extra example
```

### Запуск сервера

```bash
uv run src/server.py
```

### Запуск клиентского примера

```bash
uv run src/client.py
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_entity` | Поиск ID сущности в Wikidata по запросу |
| `search_property` | Поиск ID свойства в Wikidata по запросу |
| `get_properties` | Получение свойств, связанных с указанным ID сущности в Wikidata |
| `execute_sparql` | Выполнение SPARQL запроса к Wikidata |
| `get_metadata` | Извлечение английского названия и описания для указанного ID сущности в Wikidata |

## Возможности

- Поиск идентификаторов сущностей и свойств в Wikidata
- Извлечение метаданных, включая названия и описания
- Выполнение SPARQL запросов к Wikidata
- Получение свойств, связанных с сущностями

## Примеры использования

```
Можешь порекомендовать мне фильм режиссёра Пон Чжун-хо?
```

## Ресурсы

- [GitHub Repository](https://github.com/zzaebok/mcp-wikidata)

## Примечания

Сервер включает клиентский пример, который демонстрирует, как LLM извлекает валидные идентификаторы сущностей и свойств, выполняет SPARQL запросы и рекомендует фильмы. Лицензия MIT License.