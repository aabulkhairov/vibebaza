---
title: Intelligent Image Generator MCP сервер
description: Мощный MCP сервер, который позволяет AI-ассистентам генерировать и редактировать изображения с помощью Google Gemini 3 Pro Image с интеллектуальным улучшением промптов и продвинутыми возможностями, такими как вывод в высоком разрешении и смешивание нескольких изображений.
tags:
- AI
- Media
- API
author: shinpr
featured: false
install_command: claude mcp add mcp-image --env GEMINI_API_KEY=your-api-key --env
  IMAGE_OUTPUT_DIR=/absolute/path/to/images -- npx -y mcp-image
---

Мощный MCP сервер, который позволяет AI-ассистентам генерировать и редактировать изображения с помощью Google Gemini 3 Pro Image с интеллектуальным улучшением промптов и продвинутыми возможностями, такими как вывод в высоком разрешении и смешивание нескольких изображений.

## Установка

### NPX

```bash
npx -y mcp-image
```

## Конфигурация

### Codex

```json
[mcp_servers.mcp-image]
command = "npx"
args = ["-y", "mcp-image"]

[mcp_servers.mcp-image.env]
GEMINI_API_KEY = "your_gemini_api_key_here"
IMAGE_OUTPUT_DIR = "/absolute/path/to/images"
```

### Cursor

```json
{
  "mcpServers": {
    "mcp-image": {
      "command": "npx",
      "args": ["-y", "mcp-image"],
      "env": {
        "GEMINI_API_KEY": "your_gemini_api_key_here",
        "IMAGE_OUTPUT_DIR": "/absolute/path/to/images"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate_image` | Генерирует и редактирует изображения с помощью текстовых промптов с автоматическим улучшением промптов и поддержкой высокого... |

## Возможности

- AI-генерация изображений с использованием Gemini 3 Pro Image (Nano Banana Pro)
- Интеллектуальное улучшение промптов с помощью Gemini 2.0 Flash для превосходного качества изображений
- Редактирование изображений с естественными языковыми инструкциями и контекстно-зависимой обработкой
- Поддержка высокого разрешения для генерации изображений в 2K и 4K
- Гибкие соотношения сторон (1:1, 16:9, 9:16, 21:9 и другие)
- Смешивание нескольких изображений для композитных сцен
- Консистентность персонажей между генерациями
- Интеграция знаний о мире для точного контекста
- Множественные форматы вывода (PNG, JPEG, WebP)
- Файловый вывод с автоматическим созданием директорий

## Переменные окружения

### Обязательные
- `GEMINI_API_KEY` - API ключ для сервисов Google Gemini - получить в Google AI Studio

### Опциональные
- `IMAGE_OUTPUT_DIR` - Абсолютный путь, где будут сохраняться сгенерированные изображения (по умолчанию ./output, если не указано)
- `SKIP_PROMPT_ENHANCEMENT` - Установить в 'true' для отключения автоматической оптимизации промптов и прямой отправки промптов в генератор изображений

## Примеры использования

```
Generate a serene mountain landscape at sunset with a lake reflection
```

```
Edit this image to make the person face right
```

```
Generate a portrait of a medieval knight, maintaining character consistency for future variations
```

```
Generate a professional product photo of a smartphone with clear text on the screen
```

```
Generate a cinematic landscape of a desert at golden hour
```

## Ресурсы

- [GitHub Repository](https://github.com/shinpr/mcp-image)

## Примечания

Использует платный Gemini API как для оптимизации промптов, так и для генерации изображений. Поддерживает множественные соотношения сторон, вывод в высоком разрешении до 4K и продвинутые возможности, такие как консистентность персонажей и смешивание нескольких изображений. Изображения сохраняются как файлы с автоматическим созданием директорий. API ключ никогда не должен коммититься в систему контроля версий.