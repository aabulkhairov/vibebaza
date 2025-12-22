---
title: Vectorize MCP сервер
description: MCP сервер, который интегрируется с Vectorize.io для продвинутого векторного поиска, извлечения текста из любых форматов файлов в Markdown и возможностей приватного глубокого исследования.
tags:
- Vector Database
- AI
- Search
- Analytics
- Integration
author: vectorize-io
featured: false
---

MCP сервер, который интегрируется с Vectorize.io для продвинутого векторного поиска, извлечения текста из любых форматов файлов в Markdown и возможностей приватного глубокого исследования.

## Установка

### NPX

```bash
export VECTORIZE_ORG_ID=YOUR_ORG_ID
export VECTORIZE_TOKEN=YOUR_TOKEN
export VECTORIZE_PIPELINE_ID=YOUR_PIPELINE_ID

npx -y @vectorize-io/vectorize-mcp-server@latest
```

### Из исходников

```bash
npm install
npm run dev
```

## Конфигурация

### Ручная конфигурация VS Code

```json
{
  "mcp": {
    "inputs": [
      {
        "type": "promptString",
        "id": "org_id",
        "description": "Vectorize Organization ID"
      },
      {
        "type": "promptString",
        "id": "token",
        "description": "Vectorize Token",
        "password": true
      },
      {
        "type": "promptString",
        "id": "pipeline_id",
        "description": "Vectorize Pipeline ID"
      }
    ],
    "servers": {
      "vectorize": {
        "command": "npx",
        "args": ["-y", "@vectorize-io/vectorize-mcp-server@latest"],
        "env": {
          "VECTORIZE_ORG_ID": "${input:org_id}",
          "VECTORIZE_TOKEN": "${input:token}",
          "VECTORIZE_PIPELINE_ID": "${input:pipeline_id}"
        }
      }
    }
  }
}
```

### Claude/Windsurf/Cursor/Cline

```json
{
  "mcpServers": {
    "vectorize": {
      "command": "npx",
      "args": ["-y", "@vectorize-io/vectorize-mcp-server@latest"],
      "env": {
        "VECTORIZE_ORG_ID": "your-org-id",
        "VECTORIZE_TOKEN": "your-token",
        "VECTORIZE_PIPELINE_ID": "your-pipeline-id"
      }
    }
  }
}
```

### Конфигурация рабочего пространства VS Code

```json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "org_id",
      "description": "Vectorize Organization ID"
    },
    {
      "type": "promptString",
      "id": "token",
      "description": "Vectorize Token",
      "password": true
    },
    {
      "type": "promptString",
      "id": "pipeline_id",
      "description": "Vectorize Pipeline ID"
    }
  ],
  "servers": {
    "vectorize": {
      "command": "npx",
      "args": ["-y", "@vectorize-io/vectorize-mcp-server@latest"],
      "env": {
        "VECTORIZE_ORG_ID": "${input:org_id}",
        "VECTORIZE_TOKEN": "${input:token}",
        "VECTORIZE_PIPELINE_ID": "${input:pipeline_id}"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `retrieve` | Выполняет векторный поиск и извлекает документы из пайплайна |
| `extract` | Извлекает текст из любого формата документа и разбивает его на фрагменты в формате Markdown |
| `deep-research` | Генерирует отчёт приватного глубокого исследования из вашего пайплайна с опциональным веб-поиском |

## Возможности

- Продвинутый векторный поиск и поиск документов
- Извлечение текста и разбиение на фрагменты из любого формата файлов в Markdown
- Генерация приватных глубоких исследований
- Интеграция с пайплайнами Vectorize.io
- Интеграция веб-поиска для глубоких исследований
- Установка в один клик для VS Code

## Переменные окружения

### Обязательные
- `VECTORIZE_ORG_ID` - Ваш ID организации Vectorize
- `VECTORIZE_TOKEN` - Ваш токен аутентификации Vectorize
- `VECTORIZE_PIPELINE_ID` - Ваш ID пайплайна Vectorize

## Примеры использования

```
Financial health of the company
```

```
Generate a financial status report about the company
```

```
Extract text from a PDF document
```

```
Retrieve 5 most relevant documents about a topic
```

## Ресурсы

- [GitHub Repository](https://github.com/vectorize-io/vectorize-mcp-server)

## Примечания

Сервер обеспечивает установку в один клик для VS Code и VS Code Insiders. Он поддерживает конфигурацию как на уровне пользователя, так и на уровне рабочего пространства. Для разработки вы можете клонировать репозиторий и использовать npm команды. Процесс релиза включает обновление версии в package.json и создание git тегов.