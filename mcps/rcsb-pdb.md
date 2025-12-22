---
title: RCSB PDB MCP сервер
description: MCP сервер, который предоставляет AI-ассистентам прямой доступ к базе данных белковых структур RCSB Protein Data Bank (PDB) через интеграцию с GraphQL API, позволяя получать данные о структуре белков, экспериментальную информацию и компьютерные модели структур.
tags:
- Database
- API
- Analytics
- AI
author: QuentinCody
featured: false
---

MCP сервер, который предоставляет AI-ассистентам прямой доступ к базе данных белковых структур RCSB Protein Data Bank (PDB) через интеграцию с GraphQL API, позволяя получать данные о структуре белков, экспериментальную информацию и компьютерные модели структур.

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "rcsb-pdb": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "YOUR_RCSB_PDB_SERVER_URL_HERE"
      ]
    }
  }
}
```

## Возможности

- Получение подробной информации о конкретных записях PDB, включая экспериментальные методы
- Извлечение информации о молекулах, последовательностях и экспериментальных данных
- Запросы к компьютерным моделям структур (CSMs)
- Прямой доступ к GraphQL API PDB через разговорный AI
- Мост между AI-моделями и структурированными данными RCSB PDB

## Примеры использования

```
What is the experimental method used for PDB entry 4HHB?
```

```
Get the title and experimental method for PDB ID 1EHZ
```

```
Fetch the abstract for PDB entry 2DRI
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/rcsb-pdb-mcp-server)

## Примечания

Этот сервер предназначен для деплоя на Cloudflare Workers. Пользователям нужен URL развернутого сервера для подключения к AI-интерфейсам, таким как Cloudflare AI Playground или Claude Desktop. Основная логика находится в src/index.ts. Доступен под лицензией MIT с требованием академического цитирования для использования в исследованиях.