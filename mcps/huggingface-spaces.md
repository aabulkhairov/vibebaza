---
title: HuggingFace Spaces MCP сервер
description: MCP сервер для подключения к Hugging Face Spaces с минимальной настройкой, предоставляющий доступ к генерации изображений, моделям компьютерного зрения, синтезу речи, чат-моделям и многому другому через Claude Desktop.
tags:
- AI
- Media
- Integration
- API
- Productivity
author: Community
featured: false
---

MCP сервер для подключения к Hugging Face Spaces с минимальной настройкой, предоставляющий доступ к генерации изображений, моделям компьютерного зрения, синтезу речи, чат-моделям и многому другому через Claude Desktop.

## Установка

### NPX

```bash
npx -y @llmindset/mcp-hfspace
```

## Конфигурация

### Базовая настройка Claude Desktop

```json
{
  "mcpServers": {
    "mcp-hfspace": {
      "command": "npx",
      "args": [
        "-y",
        "@llmindset/mcp-hfspace"
      ]
    }
  }
}
```

### Расширенная настройка Claude Desktop

```json
{
  "mcpServers": {
    "mcp-hfspace": {
      "command": "npx",
      "args": [
        "-y",
        "@llmindset/mcp-hfspace",
        "--work-dir=/Users/evalstate/mcp-store",
        "shuttleai/shuttle-jaguar",
        "styletts2/styletts2",
        "Qwen/QVQ-72B-preview"
      ]
    }
  }
}
```

## Возможности

- Подключение к Hugging Face Spaces с минимальной настройкой
- Возможности генерации изображений с FLUX.1-schnell по умолчанию
- Поддержка моделей компьютерного зрения для анализа изображений
- Функции синтеза речи и распознавания речи
- Интеграция с чат-моделями
- Работа с файлами в режиме Claude Desktop
- Поддержка приватных пространств с HF токеном
- Поддержка URL-ввода
- Обработка файлов различных форматов (изображения, аудио, текст)
- Настройка рабочей директории для управления файлами

## Переменные окружения

### Опциональные
- `MCP_HF_WORK_DIR` - Рабочая директория для загрузки и скачивания файлов
- `HF_TOKEN` - Hugging Face токен для доступа к приватным пространствам
- `CLAUDE_DESKTOP_MODE` - Включение/отключение режима Claude Desktop (по умолчанию: true)

## Примеры использования

```
Сгенерируй изображение с помощью FLUX
```

```
Сравни изображения, созданные разными моделями генерации изображений
```

```
Используй paligemma, чтобы узнать, кто находится на "test_gemma.jpg"
```

```
Используй paligemma для обнаружения людей по [URL]
```

```
Создай аудио с синтезом речи
```

## Ресурсы

- [GitHub Repository](https://github.com/evalstate/mcp-hfspace)

## Примечания

Этот проект был заменен официальным Hugging Face MCP сервером. Поддерживает Gradio MCP эндпоинты с SSE потоковой передачей. Требует Claude Desktop версии 0.78 или выше. Имеет известные ограничения по таймауту с квотами ZeroGPU и жесткий лимит в 60 секунд в Claude Desktop.