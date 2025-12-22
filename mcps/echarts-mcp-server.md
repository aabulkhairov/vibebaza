---
title: ECharts MCP сервер
description: Генерируйте визуальные диаграммы с помощью Apache ECharts и AI MCP динамически для создания графиков и анализа данных с поддержкой множественных форматов экспорта и интеграцией MinIO.
tags:
- Analytics
- AI
- Integration
- Storage
- Productivity
author: Community
featured: false
---

Генерируйте визуальные диаграммы с помощью Apache ECharts и AI MCP динамически для создания графиков и анализа данных с поддержкой множественных форматов экспорта и интеграцией MinIO.

## Установка

### NPX

```bash
npx -y mcp-echarts
```

### Глобальная установка через NPM

```bash
npm install -g mcp-echarts
```

### Из исходного кода

```bash
npm install
npm run build
npm run start
```

## Конфигурация

### Claude Desktop (Mac)

```json
{
  "mcpServers": {
    "mcp-echarts": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-echarts"
      ]
    }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "mcp-echarts": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "-y",
        "mcp-echarts"
      ]
    }
  }
}
```

## Возможности

- Полная поддержка всех функций и синтаксиса ECharts, включая данные, стили, темы
- Экспорт в форматы png, svg и option с валидацией
- Интеграция MinIO для сохранения диаграмм и возврата URL вместо Base64
- Легковесный без зависимостей
- Максимально безопасный, полностью генерируется локально без удаленных сервисов
- Поддержка протоколов SSE и Streamable transport
- Множественные варианты транспорта: stdio, SSE, streamable

## Переменные окружения

### Опциональные
- `MINIO_ENDPOINT` - эндпоинт сервера MinIO
- `MINIO_PORT` - порт сервера MinIO
- `MINIO_USE_SSL` - использовать ли SSL для подключения к MinIO
- `MINIO_ACCESS_KEY` - ключ доступа MinIO
- `MINIO_SECRET_KEY` - секретный ключ MinIO
- `MINIO_BUCKET_NAME` - имя bucket MinIO для сохранения диаграмм

## Ресурсы

- [GitHub Repository](https://github.com/hustcc/mcp-echarts)

## Примечания

Доступен на множественных платформах включая modelscope, glama.ai и smithery.ai. Опции CLI включают --transport (-t) для выбора протокола, --port (-p) для указания порта и --endpoint (-e) для пользовательских эндпоинтов. Автоматически переключается на вывод Base64 если MinIO не настроен.