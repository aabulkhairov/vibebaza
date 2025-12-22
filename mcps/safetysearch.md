---
title: SafetySearch MCP сервер
description: Комплексный сервер Model Context Protocol (MCP), который предоставляет доступ к данным FDA (Управление по контролю за продуктами и лекарствами) для получения информации о безопасности пищевых продуктов, включая отзывы, предупреждения о безопасности и нежелательные события.
tags:
- Search
- Monitoring
- API
- Security
- Analytics
author: surabhya
featured: false
---

Комплексный сервер Model Context Protocol (MCP), который предоставляет доступ к данным FDA (Управление по контролю за продуктами и лекарствами) для получения информации о безопасности пищевых продуктов, включая отзывы, предупреждения о безопасности и нежелательные события.

## Установка

### Из исходников с pip

```bash
git clone https://github.com/surabhya/SafetySearch.git
cd SafetySearch
pip install "mcp[cli]>=1.0.0" httpx>=0.24.0 pydantic>=2.0.0
```

### Из исходников с uv

```bash
git clone https://github.com/surabhya/SafetySearch.git
cd SafetySearch
uv add "mcp[cli]>=1.0.0" httpx>=0.24.0 pydantic>=2.0.0
```

### Режим разработки

```bash
uv run mcp dev server.py
```

### Прямой запуск сервера

```bash
uv run python server.py
```

### Установка для Claude Desktop

```bash
uv run mcp install server.py
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_recalls_by_product_description` | Поиск отзывов продуктов питания с детальным анализом, информацией о безопасности и комплексной отчетностью |
| `search_recalls_by_product_type` | Поиск отзывов по типу продукта с детальным анализом, трендами компаний и рекомендациями по безопасности |
| `search_recalls_by_specific_product` | Проверка отзывов конкретных продуктов с детальной информацией о безопасности и рекомендациями |
| `search_recalls_by_classification` | Поиск отзывов по классификации с детальным анализом и оценкой рисков |
| `search_recalls_by_code_info` | Поиск отзывов по информации о коде с детальным отслеживанием продуктов и предупреждениями о безопасности |
| `search_recalls_by_date` | Поиск отзывов по диапазону дат с детальным анализом временной шкалы и трендов безопасности |
| `search_adverse_events_by_product` | Поиск нежелательных событий с детальным анализом случаев и информацией о безопасности |
| `get_symptom_summary_for_product` | Получение детального анализа симптомов, подробностей случаев и информации о безопасности для конкретного пищевого продукта |

## Возможности

- Проверка отзывов продуктов и предупреждений о безопасности пищевых продуктов
- Мониторинг вопросов безопасности пищевых продуктов и трендов отзывов
- Анализ трендов безопасности и информации о компаниях
- Получение комплексной информации о безопасности пищевых продуктов
- Доступ к FDA Enforcement API для данных об отзывах
- Доступ к FDA Adverse Events API для отчетов о безопасности

## Примеры использования

```
Are there any recalls for ice cream?
```

```
Show me recent recalls for bakery products.
```

```
I bought some 'Ben & Jerry's Chocolate Fudge Brownie' ice cream, is it safe?
```

```
List all the most serious food recalls.
```

```
The code on my food package is '222268'. Is there a recall for it?
```

## Ресурсы

- [GitHub Repository](https://github.com/surabhya/SafetySearch)

## Примечания

Создан с модульной архитектурой для расширяемости. Использует endpoints openFDA API для данных о контроле пищевых продуктов и нежелательных событиях. Включает комплексный набор тестов для надежности.