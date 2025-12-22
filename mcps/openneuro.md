---
title: OpenNeuro MCP сервер
description: MCP сервер, который предоставляет GraphQL доступ к API нейровизуализационных датасетов OpenNeuro для работы с данными MRI, MEG, EEG, iEEG и ECoG.
tags:
- Database
- API
- Analytics
- Search
author: QuentinCody
featured: false
---

MCP сервер, который предоставляет GraphQL доступ к API нейровизуализационных датасетов OpenNeuro для работы с данными MRI, MEG, EEG, iEEG и ECoG.

## Установка

### Из исходников

```bash
git clone https://github.com/quentincody/open-neuro-mcp-server.git
cd open-neuro-mcp-server
npm install
```

### Сервер разработки

```bash
npm run dev
```

### Деплой на Cloudflare

```bash
npm run deploy
```

## Конфигурация

### Claude Desktop (Production)

```json
{
  "mcpServers": {
    "openneuro": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://open-neuro-mcp-server.quentincody.workers.dev/sse"
      ]
    }
  }
}
```

### Claude Desktop (локальная разработка)

```json
{
  "mcpServers": {
    "openneuro": {
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
|------------|----------|
| `openneuro_graphql_query` | Выполнение GraphQL запросов к OpenNeuro API |

## Возможности

- GraphQL инструмент запросов: Выполнение GraphQL запросов к OpenNeuro API
- Интроспекция схемы: Обнаружение доступных полей и операций
- Доступ к датасетам: Запрос нейровизуализационных датасетов, снапшотов и списков файлов
- Без аутентификации: Доступ к публичным данным OpenNeuro без API ключей

## Примеры использования

```
Получить информацию о датасете по конкретному ID датасета
```

```
Список файлов в снапшоте датасета
```

```
Выполнить интроспекцию схемы для обнаружения доступных полей и операций
```

```
Запрос нейровизуализационных датасетов и их метаданных
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/open-neuro-mcp-server)

## Примечания

Этот проект доступен под MIT лицензией с требованием академического цитирования. Академическое/исследовательское использование требует цитирования, в то время как коммерческое/неакадемическое использование следует стандартным условиям MIT лицензии. Сервер работает на Cloudflare Workers и предоставляет доступ к бесплатной и открытой платформе нейровизуализационных данных OpenNeuro.