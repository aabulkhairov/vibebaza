---
title: UniProt MCP сервер
description: Комплексный MCP сервер, предоставляющий унифицированный доступ к UniProtKB и EBI Proteins API для работы с данными белковых последовательностей, функциональными аннотациями и структурной информацией с расширенными возможностями промежуточного хранения данных.
tags:
- Database
- API
- Analytics
- Cloud
- Search
author: QuentinCody
featured: false
---

Комплексный MCP сервер, предоставляющий унифицированный доступ к UniProtKB и EBI Proteins API для работы с данными белковых последовательностей, функциональными аннотациями и структурной информацией с расширенными возможностями промежуточного хранения данных.

## Установка

### NPM Install

```bash
npm install
```

### Development

```bash
npm run dev
```

### Deploy to Cloudflare

```bash
npm run deploy
```

### MCP Remote Proxy

```bash
npx mcp-remote http://localhost:8787/sse
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "uniprot": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "http://localhost:8787/sse"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `uniprot_search` | Расширенный поиск по UniProtKB с комплексной фильтрацией и пагинацией |
| `uniprot_stream` | Инструмент массовой загрузки больших наборов данных с автоматическим промежуточным хранением |
| `uniprot_entry` | Получение отдельных записей UniProtKB по номеру доступа |
| `uniprot_id_mapping` | Сопоставление ID между различными системами баз данных |
| `uniprot_blast` | Выполнение BLAST поиска по UniProtKB |
| `proteins_api_details` | Детальная информация о белках из EBI Proteins API |
| `proteins_api_features` | Особенности белковых последовательностей и аннотации |
| `proteins_api_variation` | Вариации белковых последовательностей и болезненные варианты |
| `proteins_api_proteomics` | Протеомные данные из различных исследований |
| `proteins_api_genome` | Сопоставления координат генома |
| `data_manager` | Запрос, анализ и управление промежуточно сохранёнными наборами данных |

## Возможности

- Унифицированный интерфейс для UniProt и EBI Proteins API
- Расширенное промежуточное хранение данных с использованием SQLite для сложных запросов
- Умная генерация запросов с автоматическими предложениями
- Интеллектуальное обхождение для малых наборов данных
- Масштабируемая архитектура на базе Cloudflare Workers
- Обработка API с учётом ограничений скорости
- Поддержка множественных форматов данных (JSON, TSV, FASTA, XML)
- Автоматическое создание таблиц и нормализация данных
- Массовое сопоставление ID между системами баз данных
- Возможности BLAST поиска

## Примеры использования

```
Search for human proteins: organism_id:9606 AND reviewed:true
```

```
Get protein details for accession P04637
```

```
Stage and query multiple proteins with SQL
```

```
Find cancer-related proteins and analyze with keywords
```

```
Search protein kinase family members
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/uniprot-mcp-server)

## Примечания

Построен на Cloudflare Workers с Durable Objects для масштабируемости. API ключи не требуются, поскольку как UniProt, так и EBI Proteins API имеют открытый доступ. Эндпоинты сервера доступны по адресам /mcp и /sse. Включает комплексные возможности SQL запросов для анализа промежуточно сохранённых данных.