---
title: DaVinci Resolve MCP сервер
description: MCP сервер, который подключает AI помощники для программирования (Cursor, Claude Desktop) к DaVinci Resolve, позволяя им управлять DaVinci Resolve через естественный язык.
tags:
- Media
- Integration
- AI
- Productivity
- API
author: samuelgursky
featured: true
---

MCP сервер, который подключает AI помощники для программирования (Cursor, Claude Desktop) к DaVinci Resolve, позволяя им управлять DaVinci Resolve через естественный язык.

## Установка

### Установка в один шаг (macOS)

```bash
git clone https://github.com/samuelgursky/davinci-resolve-mcp.git
cd davinci-resolve-mcp
./install.sh
```

### Установка в один шаг (Windows)

```bash
git clone https://github.com/samuelgursky/davinci-resolve-mcp.git
cd davinci-resolve-mcp
install.bat
```

### Быстрый старт (macOS)

```bash
chmod +x run-now.sh
./run-now.sh
```

### Быстрый старт (Windows)

```bash
run-now.bat
```

### Ручная установка

```bash
git clone https://github.com/samuelgursky/davinci-resolve-mcp.git
cd davinci-resolve-mcp
python -m venv venv
source venv/bin/activate  # On macOS/Linux
venv\Scripts\activate  # On Windows
pip install -r requirements.txt
```

## Конфигурация

### Cursor (macOS)

```json
{
  "mcpServers": {
    "davinci-resolve": {
      "name": "DaVinci Resolve MCP",
      "command": "/path/to/your/venv/bin/python",
      "args": [
        "/path/to/your/davinci-resolve-mcp/src/main.py"
      ]
    }
  }
}
```

### Cursor (Windows)

```json
{
  "mcpServers": {
    "davinci-resolve": {
      "name": "DaVinci Resolve MCP",
      "command": "C:\\path\\to\\venv\\Scripts\\python.exe",
      "args": ["C:\\path\\to\\davinci-resolve-mcp\\src\\main.py"]
    }
  }
}
```

## Возможности

- Получение версии DaVinci Resolve
- Получение/переключение текущей страницы (Edit, Color, Fusion и др.)
- Список доступных проектов
- Получение имени текущего проекта
- Открытие проекта по имени
- Создание нового проекта
- Сохранение текущего проекта
- Список всех таймлайнов
- Получение информации о текущем таймлайне
- Создание нового таймлайна

## Переменные окружения

### Обязательные
- `RESOLVE_SCRIPT_API` - Путь к директории scripting API DaVinci Resolve
- `RESOLVE_SCRIPT_LIB` - Путь к библиотеке fusion script DaVinci Resolve
- `PYTHONPATH` - Путь Python, включающий модули Resolve API

## Примеры использования

```
What version of DaVinci Resolve is running?
```

```
List all projects in DaVinci Resolve
```

```
Create a new timeline called 'My Sequence'
```

```
Add a marker at the current position
```

## Ресурсы

- [GitHub Repository](https://github.com/samuelgursky/davinci-resolve-mcp)

## Примечания

Требует DaVinci Resolve 18.5+ запущенный в фоне. Поддерживает macOS и Windows (Linux не поддерживается). Необходим Python 3.6+. Включает специализированные скрипты запуска для интеграции с Cursor и Claude Desktop.