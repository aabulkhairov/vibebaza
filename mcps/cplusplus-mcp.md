---
title: cplusplus-mcp MCP сервер
description: Семантический анализ C++ кода с использованием libclang. Позволяет Claude понимать кодовые базы C++ через парсинг AST вместо текстового поиска - находить классы, навигировать по наследованию, отслеживать вызовы функций и исследовать взаимосвязи в коде.
tags:
- Code
- Analytics
- API
- DevOps
- Productivity
author: Community
featured: false
---

Семантический анализ C++ кода с использованием libclang. Позволяет Claude понимать кодовые базы C++ через парсинг AST вместо текстового поиска - находить классы, навигировать по наследованию, отслеживать вызовы функций и исследовать взаимосвязи в коде.

## Установка

### Из исходного кода

```bash
git clone <repository-url>
cd CPlusPlus-MCP-Server
# Windows:
server_setup.bat
# Linux/macOS:
./server_setup.sh
```

### Тестирование установки

```bash
mcp_env\Scripts\activate
python scripts\test_installation.py
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "cpp-analyzer": {
      "command": "python",
      "args": [
        "-m",
        "mcp_server.cpp_mcp_server"
      ],
      "cwd": "YOUR_INSTALLATION_PATH_HERE",
      "env": {
        "PYTHONPATH": "YOUR_INSTALLATION_PATH_HERE"
      }
    }
  }
}
```

### Codex CLI

```json
{
  "mcpServers": {
    "cpp-analyzer": {
      "type": "stdio",
      "command": "YOUR_REPO_PATH/mcp_env/bin/python",
      "args": [
        "-m",
        "mcp_server.cpp_mcp_server"
      ],
      "env": {
        "PYTHONPATH": "YOUR_REPO_PATH"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_classes` | Поиск классов по шаблону имени |
| `search_functions` | Поиск функций по шаблону имени |
| `get_class_info` | Получение подробной информации о классе (методы, члены, наследование) |
| `get_function_signature` | Получение сигнатур функций и параметров |
| `find_in_file` | Поиск символов в определенных файлах |
| `get_class_hierarchy` | Получение полной иерархии наследования для класса |
| `get_derived_classes` | Поиск всех классов, наследующихся от базового класса |
| `find_callers` | Поиск всех функций, которые вызывают определенную функцию |
| `find_callees` | Поиск всех функций, вызываемых определенной функцией |
| `get_call_path` | Поиск путей вызовов от одной функции к другой |

## Возможности

- Контекстно-эффективный анализ C++ кода с использованием libclang
- Семантическое понимание структуры кода против простого текстового поиска
- Анализ сигнатур функций с типами и именами параметров
- Анализ членов классов, методов и наследования
- Полное отображение иерархии наследования
- Анализ графа вызовов для понимания потока кода
- Кэширование распарсенного AST для улучшения производительности
- Поддержка инкрементального анализа и поиска по всему проекту
- Настраиваемые шаблоны исключения файлов и обработка зависимостей

## Переменные окружения

### Обязательные
- `PYTHONPATH` - Путь к репозиторию для обнаружения Python модулей

## Примеры использования

```
Use the cpp-analyzer tool to set the project directory to C:\path\to\your\cpp\project
```

```
Find all classes containing 'Actor'
```

```
Show me the Component class details
```

```
What's the signature of BeginPlay function?
```

```
Search for physics-related functions
```

## Ресурсы

- [GitHub Repository](https://github.com/kandrwmrtn/cplusplus_mcp)

## Примечания

Требует Python 3.9+, LLVM's libclang (автоматически загружается скриптами установки), и начальная индексация может занимать несколько минут для больших кодовых баз. Поведение сервера можно настроить через cpp-analyzer-config.json для исключения директорий, шаблонов файлов и обработки зависимостей. Гораздо быстрее чем grep для поиска символов C++ и анализа структуры кода.