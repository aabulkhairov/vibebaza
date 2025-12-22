---
title: Figma to Flutter MCP сервер
description: MCP сервер, который объединяет дизайны Figma с Flutter кодом, извлекая подробные данные о дизайне, компонентах, экранах и ресурсах из файлов Figma, чтобы помочь AI агентам генерировать более качественные Flutter реализации.
tags:
- Code
- AI
- Integration
- Productivity
- API
author: mhmzdev
featured: true
---

MCP сервер, который объединяет дизайны Figma с Flutter кодом, извлекая подробные данные о дизайне, компонентах, экранах и ресурсах из файлов Figma, чтобы помочь AI агентам генерировать более качественные Flutter реализации.

## Установка

### NPX (MacOS/Linux)

```bash
npx -y figma-flutter-mcp --figma-api-key=YOUR-API-KEY --stdio
```

### NPX (Windows)

```bash
cmd /c npx -y figma-flutter-mcp --figma-api-key=YOUR-API-KEY --stdio
```

### Локальная разработка

```bash
git clone <your-repo-url> figma-flutter-mcp
cd figma-flutter-mcp
npm install
echo "FIGMA_API_KEY=your-figma-api-key-here" > .env
npm run dev
```

## Конфигурация

### Cursor (MacOS/Linux)

```json
{
  "mcpServers": {
    "Figma Flutter MCP": {
      "command": "npx",
      "args": ["-y", "figma-flutter-mcp", "--figma-api-key=YOUR-API-KEY", "--stdio"]
    }
  }
}
```

### Cursor (Windows)

```json
{
  "mcpServers": {
    "Figma Flutter MCP": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "figma-flutter-mcp", "--figma-api-key=YOUR-API-KEY", "--stdio"]
    }
  }
}
```

### Локальное тестирование

```json
{
  "mcpServers": {
    "local-figma-flutter": {
      "url": "http://localhost:3333/mcp"
    }
  }
}
```

## Возможности

- Извлечение данных узлов Figma: разметка, стилизация, размеры, цвета, текстовое содержимое
- Анализ структуры: дочерние элементы, вложенные компоненты, визуальная важность
- Предоставление рекомендаций по виджетам Flutter и шаблонам реализации
- Извлечение метаданных экранов: тип устройства, ориентация, размеры
- Идентификация разделов экрана: заголовок, подвал, навигация, области контента
- Анализ навигационных элементов: панели вкладок, панели приложения, выдвижные панели
- Предоставление рекомендаций по Scaffold для структуры экранов Flutter
- Экспорт изображений (.png, .jpeg, .jpg) в папку assets/
- Экспорт SVG ресурсов из векторных элементов Figma
- Извлечение темы и типографики из фреймов Figma

## Переменные окружения

### Обязательные
- `FIGMA_API_KEY` - персональный токен доступа Figma для аутентификации API

## Примеры использования

```
Setup flutter theme from <figma_link> including Colors and Typography
```

```
Create this widget in flutter from figma COMPONENT link: <figma_link>, use named constructors for variants and break the files in smaller parts for code readability
```

```
Design this intro screen from the figma link <figma_link>, ensure the code is readable by having smaller files
```

```
Export this image asset from figma link: <figma_link>
```

```
Export this as an SVG asset from Figma link: <figma_link>
```

## Ресурсы

- [GitHub Repository](https://github.com/mhmzdev/figma-flutter-mcp)

## Примечания

Требует Figma API Key (персональный токен доступа). Лучше всего подходит для MVP и небольших проектов, а не для масштабируемых приложений. Качественные дизайны Figma с автолейаутами и фреймами дают лучшие результаты. Интенсивное использование может привести к срабатыванию лимитов Figma. Сервер включает повторные попытки с задержкой, но не обходит ограничения Figma.