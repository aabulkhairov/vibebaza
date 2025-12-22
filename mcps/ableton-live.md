---
title: Ableton Live MCP сервер
description: MCP сервер для управления Ableton Live через OSC (Open Sound Control).
  Позволяет AI-ассистентам манипулировать треками, маршрутизацией и другими функциями DAW.
tags:
- Media
- Integration
- API
- Productivity
author: Simon-Kansara
featured: true
---

MCP сервер для управления Ableton Live через OSC (Open Sound Control). Позволяет AI-ассистентам манипулировать треками, маршрутизацией и другими функциями DAW.

## Установка

### Из исходников

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
git clone https://github.com/your-username/mcp_ableton_server.git
cd mcp_ableton_server
uv sync
```

### Запуск OSC Daemon

```bash
uv run osc_daemon.py
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "Ableton Live Controller": {
      "command": "/path/to/your/project/.venv/bin/python",
      "args": ["/path/to/your/project/mcp_ableton_server.py"]
    }
  }
}
```

## Возможности

- MCP-совместимый API для управления Ableton Live из MCP клиентов
- Использует python-osc для отправки и получения OSC сообщений
- Основан на OSC имплементации из AbletonOSC
- Request-response обработка команд Ableton Live
- Полный маппинг доступных OSC адресов на инструменты MCP клиентов

## Примеры использования

```
Prepare a set to record a rock band
```

```
Set the input routing channel of all tracks that have "voice" in their name to Ext. In 2
```

## Ресурсы

- [GitHub Repository](https://github.com/Simon-Kansara/ableton-live-mcp-server)

## Примечания

Требуется установить AbletonOSC как control surface. Сервер работает на localhost: MCP Socket на порту 65432, OSC send порт 11000, OSC receive порт 11001. Расположение конфигурационного файла зависит от ОС: macOS — ~/Library/Application Support/Claude/claude_desktop_config.json, Windows — %APPDATA%/Claude/claude_desktop_config.json.
