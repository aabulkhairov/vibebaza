---
title: market-fiyati MCP сервер
description: MCP сервер, который предоставляет доступ к marketfiyati.org.tr — сайту сравнения цен на продукты питания в Турции, позволяя искать товары и сравнивать цены.
tags:
- Search
- API
- Finance
- Integration
author: Community
featured: false
---

MCP сервер, который предоставляет доступ к marketfiyati.org.tr — сайту сравнения цен на продукты питания в Турции, позволяя искать товары и сравнивать цены.

## Установка

### Из исходников

```bash
git clone https://github.com/mtcnbzks/market-fiyati-mcp-server.git
cd market-fiyati-mcp-server
uv venv
uv sync
```

### Установка MCP клиента

```bash
uv run mcp install src/market_fiyati_mcp_server/server.py
```

### Запуск сервера

```bash
uv run python -m market_fiyati_mcp_server.server
```

## Конфигурация

### VS Code

```json
{
  "servers": {
    "market-fiyati": {
      "command": "uvx",
      "args": ["market-fiyati-mcp-server"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_product` | Поиск товаров по ключевым словам с возможностью фильтрации по местоположению |
| `search_product_by_identity` | Получение информации о товаре по уникальному идентификатору (например, штрих-код или внутренний ID) |
| `search_similar_products` | Поиск товаров, похожих на заданный товар по ID |

## Возможности

- Поиск товаров: находите продукты по ключевым словам
- Поиск по ID: ищите товары по их уникальному ID или штрих-коду
- Поиск похожих товаров: находите товары, похожие на выбранный
- Поиск с учетом местоположения с параметрами широты, долготы и расстояния

## Ресурсы

- [GitHub Repository](https://github.com/mtcnbzks/market-fiyati-mcp-server)

## Примечания

Требует Python 3.12+ и пакетный менеджер uv. Сервер подключается к API marketfiyati.org.tr для сравнения цен на продукты питания в Турции.