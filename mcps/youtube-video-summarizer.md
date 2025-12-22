---
title: YouTube Video Summarizer MCP сервер
description: MCP сервер, который позволяет AI-ассистентам анализировать и резюмировать YouTube видео, извлекая субтитры, описания и метаданные.
tags:
- Media
- AI
- Analytics
- API
author: nabid-pf
featured: false
---

MCP сервер, который позволяет AI-ассистентам анализировать и резюмировать YouTube видео, извлекая субтитры, описания и метаданные.

## Установка

### NPX (установка не требуется)

```bash
npx -y youtube-video-summarizer-mcp
```

### Глобальная установка

```bash
npm install -g youtube-video-summarizer-mcp
```

### Из исходного кода

```bash
git clone https://github.com/nabid-pf/youtube-video-summarizer-mcp.git
cd youtube-video-summarizer-mcp
npm install
npm run build
```

## Конфигурация

### Метод NPX

```json
{
  "mcpServers": {
    "youtube-video-summarizer": {
      "command": "npx",
      "args": ["-y", "youtube-video-summarizer-mcp"]
    }
  }
}
```

### Глобальная установка

```json
{
  "mcpServers": {
    "youtube-video-summarizer": {
      "command": "youtube-video-summarizer",
      "args": []
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-video-info-for-summary-from-url` | Извлечение информации о видео и субтитров по YouTube URL |
| `get-video-captions` | Получение субтитров для конкретного видео |
| `get-video-metadata` | Получение полных метаданных видео |

## Возможности

- Извлечение субтитров видео на нескольких языках
- Получение полных метаданных видео (название, описание, длительность)
- Предоставление структурированных данных AI-ассистентам для комплексного резюмирования видео
- Работа с любыми MCP-совместимыми клиентами через MCP интеграцию
- Поддержка различных форматов YouTube URL
- Извлечение субтитров на конкретных языках

## Примеры использования

```
Can you summarize this YouTube video: https://youtube.com/watch?v=VIDEO_ID
```

```
What are the main points from this video's captions?
```

```
Extract the key information from this YouTube link
```

## Ресурсы

- [GitHub Repository](https://github.com/nabid-pf/youtube-video-summarizer-mcp)

## Примечания

Сервер автоматически фильтрует любые выводы npm/npx для обеспечения соответствия MCP протоколу. Использует youtube-caption-extractor для извлечения субтитров и поддерживает различные форматы YouTube URL.