---
title: OpenAI GPT Image MCP сервер
description: MCP сервер для работы с API генерации и редактирования изображений OpenAI GPT-4o/gpt-image-1, поддерживающий создание изображений по текстовым запросам и расширенные возможности редактирования.
tags:
- AI
- Media
- API
- Productivity
author: SureScaleAI
featured: false
---

MCP сервер для работы с API генерации и редактирования изображений OpenAI GPT-4o/gpt-image-1, поддерживающий создание изображений по текстовым запросам и расширенные возможности редактирования.

## Установка

### Из исходного кода

```bash
git clone https://github.com/SureScaleAI/openai-gpt-image-mcp.git
cd openai-gpt-image-mcp
yarn install
yarn build
```

## Конфигурация

### Claude Desktop/VSCode/Cursor/Windsurf

```json
{
  "mcpServers": {
    "openai-gpt-image-mcp": {
      "command": "node",
      "args": ["/absolute/path/to/dist/index.js"],
      "env": { "OPENAI_API_KEY": "sk-..." }
    }
  }
}
```

### Конфигурация для Azure OpenAI

```json
{
  "mcpServers": {
    "openai-gpt-image-mcp": {
      "command": "node",
      "args": ["/absolute/path/to/dist/index.js"],
      "env": { 
        "AZURE_OPENAI_API_KEY": "sk-...",
        "AZURE_OPENAI_ENDPOINT": "my.endpoint.com",
        "OPENAI_API_VERSION": "2024-12-01-preview"
      }
    }
  }
}
```

### С файлом окружения

```json
{
  "mcpServers": {
    "openai-gpt-image-mcp": {
      "command": "node",
      "args": ["/absolute/path/to/dist/index.js", "--env-file", "./deployment/.env"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `create-image` | Генерирует изображения по запросу с расширенными опциями (размер, качество, фон и т.д.) |
| `edit-image` | Редактирует или дополняет изображения с использованием запроса и опциональной маски, поддерживает как файловые пути, так и base64 |

## Возможности

- Генерация изображений по текстовым запросам с использованием новейших моделей OpenAI
- Редактирование изображений (инпейнтинг, аутпейнтинг, композитинг) с расширенным контролем через запросы
- Поддержка Claude Desktop, Cursor, VSCode, Windsurf и любых MCP-совместимых клиентов
- Вывод в файл: сохранение сгенерированных изображений напрямую на диск или получение в формате base64
- Генерация до 10 изображений одновременно с помощью create-image
- Поддержка масок для контроля областей применения редактирования
- Автоматическое переключение на файловый вывод для больших изображений, превышающих лимит в 1MB

## Переменные окружения

### Обязательные
- `OPENAI_API_KEY` - API ключ OpenAI для доступа к API генерации изображений

### Опциональные
- `AZURE_OPENAI_API_KEY` - API ключ Azure OpenAI для развертываний Azure
- `AZURE_OPENAI_ENDPOINT` - URL эндпоинта Azure OpenAI
- `OPENAI_API_VERSION` - версия API OpenAI для развертываний Azure
- `MCP_HF_WORK_DIR` - директория для сохранения больших изображений и файловых выводов

## Ресурсы

- [Репозиторий GitHub](https://github.com/SureScaleAI/openai-gpt-image-mcp)

## Примечания

Требуется верифицированная организация OpenAI для доступа к API изображений. После верификации активация доступа к API изображений может занять 15-20 минут. MCP клиенты имеют лимит в 1MB, поэтому большие изображения автоматически сохраняются на диск. Пути к файлам должны быть абсолютными. Поддерживается конфигурация через файл окружения с флагом --env-file.