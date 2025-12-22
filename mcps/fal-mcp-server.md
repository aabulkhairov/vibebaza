---
title: Fal MCP Server MCP сервер
description: Model Context Protocol сервер, который позволяет Claude Desktop и другим MCP клиентам генерировать изображения, видео, музыку и аудио с помощью моделей Fal.ai, таких как FLUX, Stable Diffusion и MusicGen.
tags:
- AI
- Media
- API
- Integration
author: Community
featured: false
---

Model Context Protocol сервер, который позволяет Claude Desktop и другим MCP клиентам генерировать изображения, видео, музыку и аудио с помощью моделей Fal.ai, таких как FLUX, Stable Diffusion и MusicGen.

## Установка

### Docker

```bash
docker pull ghcr.io/raveenb/fal-mcp-server:latest
docker run -d --name fal-mcp -e FAL_KEY=your-api-key -p 8080:8080 ghcr.io/raveenb/fal-mcp-server:latest
```

### PyPI

```bash
pip install fal-mcp-server
```

### uv

```bash
uv pip install fal-mcp-server
```

### Из исходного кода

```bash
git clone https://github.com/raveenb/fal-mcp-server.git
cd fal-mcp-server
pip install -e .
```

## Конфигурация

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "fal-ai": {
      "command": "curl",
      "args": ["-N", "http://localhost:8080/sse"]
    }
  }
}
```

### Claude Desktop (PyPI)

```json
{
  "mcpServers": {
    "fal-ai": {
      "command": "python",
      "args": ["-m", "fal_mcp_server.server"],
      "env": {
        "FAL_KEY": "your-fal-api-key"
      }
    }
  }
}
```

### Claude Desktop (исходный код)

```json
{
  "mcpServers": {
    "fal-ai": {
      "command": "python",
      "args": ["/path/to/fal-mcp-server/src/fal_mcp_server/server.py"],
      "env": {
        "FAL_KEY": "your-fal-api-key"
      }
    }
  }
}
```

## Возможности

- Генерация изображений с помощью Flux, SDXL и других моделей
- Генерация видео из изображений или текстовых запросов
- Создание музыки по текстовому описанию
- Преобразование текста в речь
- Транскрибация аудио с помощью Whisper
- Апскейлинг изображений для повышения разрешения
- Трансформация изображений по текстовому запросу
- Нативный Async API с fal_client.run_async() для оптимальной производительности
- Поддержка очередей для длительных задач с обновлением прогресса
- Множественные режимы транспорта: STDIO, HTTP/SSE и двойной режим

## Переменные окружения

### Обязательные
- `FAL_KEY` - API ключ Fal.ai для аутентификации

## Примеры использования

```
Generate an image of a sunset
```

```
Create a video from this image
```

```
Generate 30 seconds of ambient music
```

```
Convert this text to speech
```

```
Transcribe this audio file
```

## Ресурсы

- [GitHub Repository](https://github.com/raveenb/fal-mcp-server)

## Примечания

Поддерживает множество типов моделей, включая flux_schnell, flux_dev, sdxl для изображений; svd, animatediff для видео; и musicgen, bark, whisper для аудио. Предлагает как традиционный STDIO, так и современный HTTP/SSE транспорт для веб-доступа.