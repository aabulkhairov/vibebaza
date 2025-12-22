---
title: IIIF MCP сервер
description: Комплексная поддержка протокола IIIF (International Image Interoperability Framework) для поиска, навигации и работы с цифровыми коллекциями музеев, библиотек и архивов по всему миру.
tags:
- Media
- Search
- API
- Integration
- Analytics
author: Community
featured: false
---

Комплексная поддержка протокола IIIF (International Image Interoperability Framework) для поиска, навигации и работы с цифровыми коллекциями музеев, библиотек и архивов по всему миру.

## Установка

### Стандартная установка

```bash
npm install
npm run build
```

### Одиночный файл-пакет

```bash
npm run bundle
# Создаёт iiif-mcp-bundle.js - npm install не нужен для деплоя
```

## Конфигурация

### Стандартная установка

```json
{
  "mcpServers": {
    "iiif": {
      "command": "node",
      "args": ["/path/to/mcp_iiif/dist/index.js"]
    }
  }
}
```

### Одиночный файл-пакет

```json
{
  "mcpServers": {
    "iiif": {
      "command": "node",
      "args": ["/path/to/iiif-mcp-bundle.js"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `iiif-image-fetch` | Получение фактических данных IIIF изображения с ограничениями по размеру и поддержкой регионов |
| `iiif-manifest-canvases` | Список всех холстов в манифесте с опциями фильтрации |
| `iiif-canvas-info` | Получение детальной информации о конкретных холстах |
| `iiif-search` | Поиск внутри IIIF ресурсов с использованием Content Search API |
| `iiif-manifest` | Получение метаданных манифеста из IIIF Presentation API |
| `iiif-collection` | Получение и навигация по IIIF коллекциям с поддержкой иерархических структур |
| `iiif-image` | Построение URL IIIF Image API и получение информации об изображении |
| `iiif-annotation` | Извлечение и анализ аннотаций из IIIF ресурсов, включая текстовые транскрипции, переводы... |

## Возможности

- Полнотекстовый поиск внутри IIIF документов с поддержкой Search API v0, v1 и v2
- Поддержка форматов IIIF Presentation API v2 и v3
- Операции с изображениями с параметрами региона, размера, поворота, качества и формата
- Полная реализация IIIF Authorization Flow API с управлением сессиями
- Поддержка аудио/видео контента с расчётом длительности и навигацией по главам
- Управление коллекциями с иерархической навигацией по вложенным коллекциям
- Операции с аннотациями с многоязычной поддержкой и фильтрацией
- Отслеживание изменений через Change Discovery API с навигацией по потоку активности
- Поддержка структурированного вывода для интеграции с другими MCP серверами
- Упаковка в одиночный файл с помощью esbuild для деплоя без npm

## Примеры использования

```
Search for 'Paris' in Harvard's IIIF collection
```

```
Fetch a cropped and resized image from an IIIF server
```

```
List all canvases in a manuscript with annotations
```

```
Get detailed information about a specific canvas including image dimensions
```

```
Navigate through a collection's hierarchical structure
```

## Ресурсы

- [GitHub Repository](https://github.com/code4history/IIIF_MCP)

## Примечания

Сервер был протестирован с IIIF коллекциями NC State University и успешно развёрнут в Claude Desktop. Все инструменты поддерживают структурированный вывод для лучшей интеграции с другими MCP серверами и программной обработки. Версия 1.1.0 представляет возможности получения данных изображений и улучшенной навигации по холстам.