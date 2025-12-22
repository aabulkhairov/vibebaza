---
title: mcp-vision MCP сервер
description: MCP сервер, предоставляющий доступ к моделям компьютерного зрения HuggingFace (таким как zero-shot детекция объектов) в виде инструментов, что расширяет возможности больших языковых моделей и моделей зрение-язык.
tags:
- AI
- Media
- Analytics
- API
author: groundlight
featured: false
---

MCP сервер, предоставляющий доступ к моделям компьютерного зрения HuggingFace (таким как zero-shot детекция объектов) в виде инструментов, что расширяет возможности больших языковых моделей и моделей зрение-язык.

## Установка

### Сборка Docker

```bash
git clone git@github.com:groundlight/mcp-vision.git
cd mcp-vision
make build-docker
```

### Из исходного кода

```bash
uv install
uv run python mcp_vision
```

### Запуск Docker CPU

```bash
make run-docker-cpu
```

### Запуск Docker GPU

```bash
make run-docker-gpu
```

## Конфигурация

### Claude Desktop (GPU)

```json
"mcpServers": {
  "mcp-vision": {
    "command": "docker",
    "args": ["run", "-i", "--rm", "--runtime=nvidia", "--gpus", "all", "mcp-vision"],
	"env": {}
  }
}
```

### Claude Desktop (CPU)

```json
"mcpServers": {
  "mcp-vision": {
    "command": "docker",
    "args": ["run", "-i", "--rm", "mcp-vision"],
	"env": {}
  }
}
```

### Claude Desktop (публичный образ)

```json
"mcpServers": {
  "mcp-vision": {
    "command": "docker",
    "args": ["run", "-i", "--rm", "--runtime=nvidia", "--gpus", "all", "groundlight/mcp-vision:latest"],
	"env": {}
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `locate_objects` | Обнаружение и локализация объектов на изображении с использованием zero-shot pipelines детекции объектов от HuggingFace |
| `zoom_to_object` | Увеличение объекта на изображении путем обрезки по границам объекта для более детального анализа |

## Возможности

- Zero-shot детекция объектов с использованием моделей HuggingFace
- Поддержка вычислений как на CPU, так и на GPU
- Определение местоположения объектов с ограничивающими рамками
- Обрезка изображений для увеличения обнаруженных объектов
- Поддержка пользовательских моделей HuggingFace
- Контейнеризированный деплой с Docker

## Примеры использования

```
From the information on that advertising board, what is the type of this shop? Options: The shop is a yoga studio. The shop is a cafe. The shop is a seven-eleven. The shop is a milk tea shop.
```

## Ресурсы

- [GitHub Repository](https://github.com/groundlight/mcp-vision)

## Примечания

Репозиторий находится в активной разработке. При работе на CPU модель детекции объектов большого размера по умолчанию может долго загружаться и выполнять инференс. Рассмотрите возможность использования меньшей модели. Если вы загружаете изображения напрямую в Claude вместо предоставления ссылок для скачивания, он не сможет вызывать инструменты. Отключите веб-поиск для лучших результатов, поскольку Claude предпочтет веб-поиск локальным MCP инструментам.