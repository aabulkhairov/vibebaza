---
title: CCTV VMS MCP сервер
description: MCP сервер, который подключается к системам записи CCTV (VMS) для получения записанных и живых видеопотоков, а также управления ПО VMS, включая диалоги прямого эфира и воспроизведения.
tags:
- Security
- Media
- Monitoring
- Integration
- API
author: jyjune
featured: false
---

MCP сервер, который подключается к системам записи CCTV (VMS) для получения записанных и живых видеопотоков, а также управления ПО VMS, включая диалоги прямого эфира и воспроизведения.

## Установка

### UV Package Manager

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Установка VMS сервера

```bash
Download and install from: http://surveillance-logic.com/en/download.html
```

### Python зависимости

```bash
Download vmspy library: https://sourceforge.net/projects/security-vms/files/vmspy1.4-python3.12-x64.zip/download
Extract contents into mcp_vms directory
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "vms": {
      "command": "uv",
      "args": [
        "--directory",
        "X:\\path\\to\\mcp-vms",
        "run",
        "mcp_vms.py"
      ]
    }
  }
}
```

### Подключение к VMS

```json
vms_config = {
    'img_width': 320,
    'img_height': 240,
    'pixel_format': 'RGB',
    'url': '127.0.0.1',
    'port': 3300,
    'access_id': 'admin',
    'access_pw': 'admin',
}
```

## Возможности

- Получение информации о видеоканалах, включая статус подключения и записи
- Получение дат и времени записи для конкретных каналов
- Получение живых или записанных изображений с видеоканалов
- Показ прямых видеопотоков или диалогов воспроизведения для конкретных каналов и временных меток
- Управление PTZ (Pan-Tilt-Zoom) камерами путем перемещения их в заданные позиции
- Комплексная обработка ошибок и логирование

## Ресурсы

- [GitHub Repository](https://github.com/jyjune/mcp_vms)

## Примечания

Требует Python 3.12+, библиотеку vmspy и библиотеку Pillow. Необходимо установить VMS сервер перед использованием данного MCP сервера. Структура директории должна включать файлы vmspy.pyd и FFmpeg DLL.