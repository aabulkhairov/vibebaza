---
title: Transcribe MCP сервер
description: MCP сервер, который предоставляет быстрые и надежные транскрипции аудио/видео файлов и голосовых заметок, позволяя LLM взаимодействовать с текстовым содержимым аудио/видео файлов через Transcribe.com.
tags:
- AI
- Media
- Productivity
- Integration
- API
author: transcribe-app
featured: false
---

MCP сервер, который предоставляет быстрые и надежные транскрипции аудио/видео файлов и голосовых заметок, позволяя LLM взаимодействовать с текстовым содержимым аудио/видео файлов через Transcribe.com.

## Установка

### MCPB Bundle (Claude Desktop)

```bash
Download pre-built MCP Bundle from https://transcribe.com/mcp-integration#jumpto=mcp_download_mcpb
Double-click the .mcpb file for automatic installation
```

### NPX (Другие ассистенты)

```bash
npx -y github:transcribe-app/mcp-transcribe
```

## Конфигурация

### Другие ассистенты

```json
{
  "key": "transcribe-local",
  "command": "npx",
  "args": [
    "args": ["-y", "github:transcribe-app/mcp-transcribe"],
  ],
  "env": {
    "MCP_INTEGRATION_URL": "<your-MCP-integration-URL>"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `convert-to-text` | Конвертирует аудио в текст и возвращает текст немедленно. Использует временные кредиты и поддерживает как URL... |
| `get-balance` | Возвращает баланс вашего аккаунта. |
| `read-transcriptions` | Возвращает содержимое готовых транскрипций с опциональной фильтрацией/поиском. |
| `update-transcription` | Переименовывает или удаляет транскрипции в вашем аккаунте на Transcribe.com. |

## Возможности

- Быстрый, легковесный и дружелюбный к LLM с результатами за секунды
- Высококачественные транскрипции с поддержкой зашумленного аудио
- Поддержка более 100 языков
- Временные метки на уровне слов и разделение говорящих
- Широкий спектр форматов из коробки
- Облачное хранилище для аудио заметок и записей
- Поддержка совместной работы через функцию команд Transcribe.com
- Установка в один клик в Claude Desktop
- Автоматическое управление зависимостями
- Встроенная обработка ошибок и отладка

## Переменные окружения

### Обязательные
- `MCP_INTEGRATION_URL` - Приватный URL интеграции MCP, полученный из приложения Transcribe.com

## Ресурсы

- [GitHub Repository](https://github.com/transcribe-app/mcp-transcribe)

## Примечания

Требует приватный URL интеграции MCP из аккаунта Transcribe.com. Сервер поддерживает как удаленные публичные URL, так и локальные пути к файлам для транскрипции. Храните ваш приватный URL безопасно и не делитесь им с другими.