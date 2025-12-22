---
title: Video Editor MCP сервер
description: MCP сервер для загрузки, редактирования, поиска и генерации видео с использованием API Video Jungle. Поддерживает мультимодальный анализ и возможности редактирования видео.
tags:
- Media
- AI
- Analytics
- API
- Search
author: Community
featured: false
install_command: npx -y @smithery/cli install video-editor-mcp --client claude
---

MCP сервер для загрузки, редактирования, поиска и генерации видео с использованием API Video Jungle. Поддерживает мультимодальный анализ и возможности редактирования видео.

## Установка

### Smithery

```bash
npx -y @smithery/cli install video-editor-mcp --client claude
```

### Прямая установка

```bash
uv run video-editor-mcp YOURAPIKEY
```

### С доступом к фотографиям

```bash
LOAD_PHOTOS_DB=1 uv run video-editor-mcp YOURAPIKEY
```

## Конфигурация

### Claude Desktop (Опубликованная версия)

```json
{
  "mcpServers": {
    "video-editor-mcp": {
      "command": "uvx",
      "args": [
        "video-editor-mcp",
        "YOURAPIKEY"
      ]
    }
  }
}
```

### Claude Desktop (Версия для разработки)

```json
{
  "mcpServers": {
    "video-editor-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "/Users/YOURDIRECTORY/video-editor-mcp",
        "run",
        "video-editor-mcp",
        "YOURAPIKEY"
      ]
    }
  }
}
```

### Claude Desktop (С доступом к фотографиям)

```json
{
  "video-jungle-mcp": {
    "command": "uv",
    "args": [
      "--directory",
      "/Users/<PATH_TO>/video-jungle-mcp",
      "run",
      "video-editor-mcp",
      "<YOURAPIKEY>"
    ],
    "env": {
      "LOAD_PHOTOS_DB": "1"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `add-video` | Добавляет видеофайл для анализа по URL. Возвращает vj:// URI для ссылки на видеофайл |
| `create-videojungle-project` | Создаёт проект Video Jungle для хранения генеративных скриптов, проанализированных видео и изображений |
| `edit-locally` | Создаёт проект OpenTimelineIO и загружает его на вашу машину для открытия в DaVinci Resolve Studio |
| `generate-edit-from-videos` | Генерирует отрендеренную видеомонтажную работу из набора видеофайлов |
| `generate-edit-from-single-video` | Создаёт монтаж из одного входного видеофайла |
| `get-project-assets` | Получает ресурсы проекта для генерации видеомонтажа |
| `search-videos` | Возвращает совпадения видео на основе эмбеддингов и ключевых слов |
| `update-video-edit` | Живое обновление информации о видеомонтаже. Если Video Jungle открыт, монтаж обновляется в реальном времени |

## Возможности

- Загрузка и анализ видео по URL с мультимодальным анализом
- Поиск видео с использованием эмбеддингов и ключевых слов
- Генерация видеомонтажей из множества видеофайлов
- Создание монтажей из одного видеофайла
- Интеграция с DaVinci Resolve Studio через OpenTimelineIO
- Обновления видеомонтажа в реальном времени
- Пользовательская схема URI vj:// для видеоресурсов
- Поиск видео в локальном приложении Фото (macOS)
- Организация видео и ресурсов на основе проектов

## Переменные окружения

### Опциональные
- `LOAD_PHOTOS_DB` - Установите в '1' для включения поиска видео в локальном приложении Фото на macOS

## Примеры использования

```
можешь скачать видео по адресу https://www.youtube.com/shorts/RumgYaH5XYw и назвать его fly traps?
```

```
можешь найти в моих видео fly traps?
```

```
можешь найти в моих локальных видеофайлах Skateboard?
```

```
можешь создать монтаж всех моментов, когда в видео говорят "fly trap"?
```

```
можешь создать монтаж всех моментов, когда в этом видео произносят слово "fly trap"?
```

## Ресурсы

- [GitHub репозиторий](https://github.com/burningion/video-editing-mcp)

## Примечания

Требуется аккаунт Video Jungle и API ключ с https://app.video-jungle.com/profile/settings. DaVinci Resolve Studio должен быть запущен перед использованием инструмента edit-locally. Мультимодальный анализ поддерживает как аудио, так и визуальные компоненты для поисковых запросов.