---
title: Apple Docs MCP сервер
description: MCP сервер, который обеспечивает бесшовный доступ к документации Apple
  Developer, включая фреймворки, API, SwiftUI, UIKit, видео WWDC и примеры кода
  через запросы на естественном языке с поддержкой ИИ.
tags:
- Search
- API
- Code
- Productivity
- Integration
author: Community
featured: false
install_command: claude mcp add apple-docs -- npx -y @kimsungwhee/apple-docs-mcp@latest
---

MCP сервер, который обеспечивает бесшовный доступ к документации Apple Developer, включая фреймворки, API, SwiftUI, UIKit, видео WWDC и примеры кода через запросы на естественном языке с поддержкой ИИ.

## Установка

### NPX

```bash
npx -y @kimsungwhee/apple-docs-mcp
```

### Глобальная установка (pnpm)

```bash
pnpm add -g @kimsungwhee/apple-docs-mcp
```

### Глобальная установка (npm)

```bash
npm install -g @kimsungwhee/apple-docs-mcp
```

### Из исходного кода

```bash
git clone https://github.com/kimsungwhee/apple-docs-mcp.git
cd apple-docs-mcp
pnpm install && pnpm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "apple-docs": {
      "command": "npx",
      "args": ["-y", "@kimsungwhee/apple-docs-mcp"]
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "apple-docs": {
      "command": "npx",
      "args": ["-y", "@kimsungwhee/apple-docs-mcp"]
    }
  }
}
```

### VS Code

```json
{
  "mcp": {
    "servers": {
      "apple-docs": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "@kimsungwhee/apple-docs-mcp"]
      }
    }
  }
}
```

### Windsurf

```json
{
  "mcpServers": {
    "apple-docs": {
      "command": "npx",
      "args": ["-y", "@kimsungwhee/apple-docs-mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_apple_docs` | Поиск по документации Apple Developer через официальный API поиска, поиск конкретных API, классов, методов |
| `get_apple_doc_content` | Получение детального содержимого документации с доступом к JSON API, опциональный расширенный анализ |
| `list_technologies` | Обзор всех технологий Apple с фильтрацией по категориям, поддержка языков, статус бета-версий |
| `search_framework_symbols` | Поиск символов в конкретном фреймворке, включая классы, структуры, протоколы с шаблонами подстановки |
| `get_related_apis` | Поиск связанных API через наследование, соответствие и связи "См. также" |
| `resolve_references_batch` | Пакетное разрешение ссылок API, извлечение и разрешение всех ссылок из документации |
| `get_platform_compatibility` | Анализ совместимости платформ, включая поддержку версий, статус бета-версий, информация об устаревших функциях |
| `find_similar_apis` | Поиск похожих API используя официальные рекомендации Apple и группировки по темам |
| `get_documentation_updates` | Отслеживание обновлений документации Apple, включая анонсы WWDC и заметки о выпусках |
| `get_technology_overviews` | Получение обзоров технологий и исчерпывающих руководств с иерархической навигацией |
| `get_sample_code` | Просмотр примеров кода Apple с фильтрацией по фреймворкам и поиском по ключевым словам |
| `search_wwdc_videos` | Поиск видеосессий WWDC с поиском по ключевым словам и фильтрацией по темам/годам |
| `get_wwdc_video_details` | Получение деталей видео WWDC с полными транскриптами, примерами кода и ресурсами |
| `list_wwdc_topics` | Список всех доступных тем WWDC по 19 категориям |
| `list_wwdc_years` | Список всех доступных годов WWDC с годами конференций и количеством видео |

## Возможности

- Умный поиск по документации Apple Developer для SwiftUI, UIKit, Foundation, CoreData, ARKit и многого другого
- Полный доступ к документации с полным доступом к JSON API Apple
- Просмотр индекса фреймворков для iOS, macOS, watchOS, tvOS, visionOS
- Исследование каталога технологий, включая SwiftUI, UIKit, Metal, Core ML, Vision и ARKit
- Отслеживание обновлений документации для анонсов WWDC 2024/2025 и последних релизов SDK
- Обзоры технологий с исчерпывающими руководствами для платформ разработки Swift, SwiftUI, UIKit
- Библиотека примеров кода с примерами Swift и Objective-C для кроссплатформенной разработки
- Библиотека видео WWDC с поиском по сессиям 2014-2025 с транскриптами и примерами кода
- Обнаружение связанных API для SwiftUI views, UIKit контроллеров и связей фреймворков
- Анализ совместимости платформ для iOS 13+, macOS 10.15+, watchOS 6+, tvOS 13+, visionOS

## Примеры использования

```
Search for SwiftUI animations
```

```
Find withAnimation API documentation
```

```
Look up async/await patterns in Swift
```

```
Show me UITableView delegate methods
```

```
Search Core Data NSPersistentContainer examples
```

## Ресурсы

- [GitHub Repository](https://github.com/kimsungwhee/apple-docs-mcp)

## Примечания

Все данные видео WWDC (2014-2025) включены непосредственно в npm пакет для нулевой задержки сети и автономного доступа. Поддерживает кэширование в памяти, умный пул UserAgent и комплексную обработку ошибок. Поддерживает несколько языков (английский, японский, корейский, китайский).