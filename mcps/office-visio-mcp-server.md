---
title: Office-Visio-MCP-Server MCP сервер
description: MCP сервер, который предоставляет инструменты для создания и редактирования диаграмм Microsoft Visio программным способом через стандартизированное API с использованием Python и COM интерфейса.
tags:
- Productivity
- API
- Integration
- Code
- Analytics
author: GongRzhe
featured: false
---

MCP сервер, который предоставляет инструменты для создания и редактирования диаграмм Microsoft Visio программным способом через стандартизированное API с использованием Python и COM интерфейса.

## Установка

### Из исходного кода

```bash
pip install pywin32
pip install mcp-server
# Clone or download repository
python visio_mcp_server.py
```

### UVX

```bash
uvx --from office-visio-mcp-server visio_mcp_server
```

## Конфигурация

### Локальный Python сервер

```json
{
  "mcpServers": {
    "ppt": {
      "command": "python",
      "args": ["/path/to/ppt_mcp_server.py"],
      "env": {}
    }
  }
}
```

### Использование UVX

```json
{
  "mcpServers": {
    "ppt": {
      "command": "uvx",
      "args": [
        "--from", "office-visio-mcp-server", "visio_mcp_server"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_visio_file` | Создает новую диаграмму Visio с опциональным шаблоном и путем сохранения |
| `open_visio_file` | Открывает существующую диаграмму Visio |
| `add_shape` | Добавляет фигуру в диаграмму Visio с указанным типом, позицией и размерами |
| `connect_shapes` | Соединяет две фигуры в диаграмме Visio с различными типами соединителей |
| `add_text` | Добавляет текст к фигуре в диаграмме Visio |
| `list_shapes` | Выводит список всех фигур в диаграмме Visio |

## Возможности

- Создание новых диаграмм Visio
- Открытие существующих диаграмм Visio
- Добавление различных фигур (Прямоугольник, Круг, Линия и т.д.)
- Соединение фигур с различными типами соединителей
- Добавление текста к фигурам
- Вывод списка всех фигур в документе
- Сохранение документов в указанные места
- Экспорт диаграмм как изображений
- Безопасное закрытие документов

## Примеры использования

```
Create a flowchart diagram with rectangles and circles
```

```
Connect shapes with straight, dynamic, or curved connectors
```

```
Add text labels to diagram shapes
```

```
Build organizational charts programmatically
```

```
Create process flow diagrams with automated connections
```

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/Office-Visio-MCP-Server)

## Примечания

Требует операционную систему Windows и установленный Microsoft Visio (Professional или Standard). Использует COM интерфейс Microsoft для автоматизации Visio. Поддерживает Python 3.12+.