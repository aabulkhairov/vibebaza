---
title: lucid-mcp-server MCP сервер
description: MCP сервер для интеграции с Lucid App, который позволяет мультимодальным LLM получать доступ, искать и анализировать диаграммы Lucid (LucidChart, LucidSpark, LucidScale) через визуальный экспорт и анализ с помощью ИИ.
tags:
- Productivity
- AI
- Integration
- Analytics
- API
author: Community
featured: false
install_command: npx -y @smithery/cli install @smartzan63/lucid-mcp-server --client
  claude
---

MCP сервер для интеграции с Lucid App, который позволяет мультимодальным LLM получать доступ, искать и анализировать диаграммы Lucid (LucidChart, LucidSpark, LucidScale) через визуальный экспорт и анализ с помощью ИИ.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @smartzan63/lucid-mcp-server --client claude
```

### NPM Global

```bash
npm install -g lucid-mcp-server
```

### MCP Inspector

```bash
npx @modelcontextprotocol/inspector lucid-mcp-server
```

## Конфигурация

### Ручная настройка VS Code

```json
{
  "mcp": {
    "servers": {
      "lucid-mcp-server": {
        "type": "stdio",
        "command": "lucid-mcp-server",
        "env": {
          "LUCID_API_KEY": "${input:lucid_api_key}",
          "AZURE_OPENAI_API_KEY": "${input:azure_openai_api_key}",
          "AZURE_OPENAI_ENDPOINT": "${input:azure_openai_endpoint}",
          "AZURE_OPENAI_DEPLOYMENT_NAME": "${input:azure_openai_deployment_name}",
          "OPENAI_API_KEY": "${input:openai_api_key}",
          "OPENAI_MODEL": "${input:openai_model}"
        }
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search-documents` | Показывает список документов в вашем аккаунте Lucid с возможностью фильтрации по ключевым словам |
| `get-document` | Получает метаданные документа и может дополнительно выполнять ИИ-анализ его визуального содержимого |
| `get-document-tabs` | Получает легковесные метаданные о всех вкладках (страницах) в документе Lucid без загрузки полного содержимого |

## Возможности

- Обнаружение документов и получение метаданных из LucidChart, LucidSpark и LucidScale
- Легковесные метаданные вкладок для быстрого просмотра структуры документа
- Экспорт PNG изображений из диаграмм Lucid
- Анализ диаграмм с помощью ИИ и мультимодальных LLM (поддерживает Azure OpenAI и OpenAI)
- Управление API ключами через переменные окружения с автоматическим переключением с Azure на OpenAI
- Реализация на TypeScript с полным покрытием тестами
- Интеграция с MCP Inspector для удобного тестирования

## Переменные окружения

### Обязательные
- `LUCID_API_KEY` - API ключ с портала разработчиков Lucid для доступа к сервисам Lucid

### Опциональные
- `AZURE_OPENAI_API_KEY` - API ключ Azure OpenAI для анализа диаграмм с помощью ИИ (имеет приоритет над OpenAI)
- `AZURE_OPENAI_ENDPOINT` - URL эндпоинта Azure OpenAI
- `AZURE_OPENAI_DEPLOYMENT_NAME` - Название деплоя Azure OpenAI (например, gpt-4o)
- `OPENAI_API_KEY` - API ключ OpenAI, используется как резервный вариант, если Azure не настроен
- `OPENAI_MODEL` - Модель OpenAI для использования (по умолчанию gpt-4o)

## Примеры использования

```
Покажи все мои документы Lucid
```

```
Получи информацию о документе с ID: [document-id]
```

```
Проанализируй эту диаграмму: [document-id]
```

```
Что показывает эта диаграмма Lucid: [document-id]
```

## Ресурсы

- [GitHub Repository](https://github.com/smartzan63/lucid-mcp-server)

## Примечания

Сервер автоматически использует Azure OpenAI, если установлен AZURE_OPENAI_API_KEY, иначе переключается на OpenAI. Для базовых операций с документами требуется только API ключ Lucid - для функций анализа с помощью ИИ необходима настройка Azure OpenAI или OpenAI.