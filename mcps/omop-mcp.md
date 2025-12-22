---
title: OMOP MCP сервер
description: MCP сервер для сопоставления клинической терминологии с концепциями Observational Medical Outcomes Partnership (OMOP) с использованием больших языковых моделей для стандартизации медицинских данных.
tags:
- Database
- AI
- Analytics
- API
- Integration
author: OHNLP
featured: false
---

MCP сервер для сопоставления клинической терминологии с концепциями Observational Medical Outcomes Partnership (OMOP) с использованием больших языковых моделей для стандартизации медицинских данных.

## Установка

### Из исходного кода

```bash
git clone https://github.com/OHNLP/omop_mcp.git
cd omop_mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "omop_mcp": {
      "command": "uv",
      "args": ["--directory", "<path-to-local-repo>", "run", "omop_mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `find_omop_concept` | Сопоставляет клиническую терминологию с концепциями OMOP, валидирует терминологические сопоставления, ищет в словаре OMOP... |

## Возможности

- Сопоставление клинической терминологии с концепциями OMOP
- Валидация терминологических сопоставлений
- Поиск в словаре OMOP
- Конвертация между различными системами клинической кодировки

## Переменные окружения

### Опциональные
- `AZURE_OPENAI_ENDPOINT` - эндпоинт сервиса Azure OpenAI
- `AZURE_OPENAI_API_KEY` - API ключ Azure OpenAI
- `AZURE_API_VERSION` - версия Azure API
- `MODEL_NAME` - имя модели Azure OpenAI
- `OPENAI_API_KEY` - OpenAI API ключ (альтернатива Azure)

## Примеры использования

```
Map `Temperature Temporal Scanner - RR` for `measurement_concept_id` in the `measurement` table.
```

```
Map clinical terms with preferred vocabularies in order of priority (e.g., "SNOMED preferred" or "LOINC > SNOMED > RxNorm")
```

## Ресурсы

- [GitHub Repository](https://github.com/OHNLP/omop_mcp)

## Примечания

Требует менеджер пакетов uv. Рекомендуется указывать поле и название таблицы OMOP в промптах для улучшения точности. Обратитесь к omop_concept_id_fields.json для списка полей и таблиц OMOP, которые хранят идентификаторы концепций. Переменные окружения нужны только для API вызовов.