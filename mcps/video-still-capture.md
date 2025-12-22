---
title: Video Still Capture MCP сервер
description: MCP сервер, который предоставляет AI-ассистентам возможность получать доступ к веб-камерам и видеоисточникам через OpenCV для захвата статичных изображений.
tags:
- Media
- AI
- Integration
- Productivity
author: Community
featured: false
install_command: mcp install videocapture_mcp.py
---

MCP сервер, который предоставляет AI-ассистентам возможность получать доступ к веб-камерам и видеоисточникам через OpenCV для захвата статичных изображений.

## Установка

### Из исходного кода

```bash
git clone https://github.com/13rac1/videocapture-mcp.git
cd videocapture-mcp
pip install -e .
```

### Запуск сервера

```bash
mcp dev videocapture_mcp.py
```

### Установка через MCP CLI

```bash
mcp install videocapture_mcp.py
```

## Конфигурация

### Claude Desktop macOS/Linux

```json
{
  "mcpServers": {
    "VideoCapture ": {
      "command": "uv",
      "args": [
        "run",
        "--with",
        "mcp[cli]",
        "--with",
        "numpy",
        "--with",
        "opencv-python",
        "mcp",
        "run",
        "/ABSOLUTE_PATH/videocapture_mcp.py"
      ]
    }
  }
}
```

### Claude Desktop Windows

```json
{
  "mcpServers": {
    "VideoCapture": {
      "command": "uv",
      "args": [
        "run",
        "--with",
        "mcp[cli]",
        "--with",
        "numpy",
        "--with",
        "opencv-python",
        "mcp",
        "run",
        "C:\ABSOLUTE_PATH\videocapture-mcp\videocapture_mcp.py"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `quick_capture` | Быстро открывает камеру, захватывает один кадр и закрывает её |
| `open_camera` | Открывает соединение с камерой |
| `capture_frame` | Захватывает один кадр из указанного видеоисточника |
| `get_video_properties` | Получает свойства видеоисточника (ширина, высота, fps и т.д.) |
| `set_video_property` | Устанавливает свойство видеоисточника (яркость, контрастность, разрешение) |
| `close_connection` | Закрывает видеосоединение и освобождает ресурсы |
| `list_active_connections` | Список всех активных видеосоединений |

## Возможности

- Быстрый захват изображений: захват одного изображения с веб-камеры без управления соединениями
- Управление соединениями: открытие, управление и закрытие соединений с камерой
- Свойства видео: чтение и настройка параметров камеры, таких как яркость, контрастность и разрешение
- Обработка изображений: базовые преобразования изображений, например горизонтальное отражение
- Несколько камер: поддержка доступа к различным камерам по индексу
- Управление ресурсами: автоматическая очистка ресурсов камеры

## Примеры использования

```
I'll take a photo using your webcam
```

```
I'll open a connection to your webcam so we can take multiple photos
```

```
Let me increase the brightness of the webcam feed
```

```
Take a photo or perform any webcam-related task
```

## Ресурсы

- [GitHub Repository](https://github.com/13rac1/videocapture-mcp)

## Примечания

Требования включают Python 3.10+, OpenCV (opencv-python), MCP Python SDK и опционально UV. Сервер предоставляет только захват статичных изображений - возможности захвата видео нет. На некоторых системах может потребоваться явное разрешение для доступа к камере.