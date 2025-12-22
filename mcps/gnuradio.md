---
title: Gnuradio MCP сервер
description: Machine Control Protocol (MCP) сервер для GNURadio, который обеспечивает программное,
  автоматизированное и AI-управляемое создание и модификацию GNURadio flowgraph'ов и .grc
  файлов.
tags:
- AI
- Code
- Integration
- API
- DevOps
author: yoelbassin
featured: false
---

Machine Control Protocol (MCP) сервер для GNURadio, который обеспечивает программное, автоматизированное и AI-управляемое создание и модификацию GNURadio flowgraph'ов и .grc файлов.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yoelbassin/gr-mcp
cd gr-mcp
uv venv --system-site-packages
```

### Установка для разработки

```bash
pip install -e ".[dev]"
pytest
```

## Конфигурация

### Claude Desktop/Cursor

```json
"mcpServers": {
  "gr-mcp": {
    "command": "uv",
    "args": [
      "--directory",
      "/path/to/gr-mcp",
      "run",
      "main.py"
    ]
  }
}
```

## Возможности

- MCP API: Предоставляет надёжный MCP интерфейс для GNURadio
- Программное создание Flowgraph'ов: Создавайте, редактируйте и сохраняйте .grc файлы из кода или автоматизации
- Готовность к LLM и автоматизации: Разработан для интеграции с AI и автоматизацией
- Расширяемость: Модульная архитектура для лёгкого расширения и настройки
- Примеры Flowgraph'ов: Включает готовые к использованию .grc примеры в директории misc/
- Протестировано: Комплексные unit тесты с pytest

## Ресурсы

- [GitHub Repository](https://github.com/yoelbassin/gnuradioMCP)

## Примечания

Требует Python >= 3.13, GNURadio (протестировано с v3.10.12.0) и менеджер пакетов UV. Флаг --system-site-packages обязателен при создании UV окружения, поскольку GNURadio устанавливает Python пакет gnuradio глобально. Проект находится в активной разработке с развивающимся API.