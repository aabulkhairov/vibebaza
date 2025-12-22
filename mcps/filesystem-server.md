---
title: FileSystem Server MCP сервер
description: Локальный MCP сервер для Visual Studio 2022, который предоставляет выборочный доступ к папкам и файлам проекта в файловой системе. Оптимизирован для локальных сред разработки без сложных настроек рабочего пространства.
tags:
- Code
- Productivity
- DevOps
- Storage
- Integration
author: Oncorporation
featured: false
---

Локальный MCP сервер для Visual Studio 2022, который предоставляет выборочный доступ к папкам и файлам проекта в файловой системе. Оптимизирован для локальных сред разработки без сложных настроек рабочего пространства.

## Установка

### Из исходного кода

```bash
uv sync
```

## Конфигурация

### Visual Studio 2022 - Базовая

```json
{
  "servers": {
    "filesystem-server": {
      "command": "python",
      "args": [
        "/absolute/path/to/your/project/filesystem_server/app.py"
      ],
      "cwd": "/absolute/path/to/your/project/filesystem_server"
    }
  }
}
```

### Visual Studio 2022 - С аргументами

```json
{
  "servers": {
    "filesystem-server": {
      "command": "python",
      "args": [
        "/absolute/path/to/your/project/filesystem_server/app.py",
        "--allowed-dirs", "D:/projects", "D:/Webs",
        "--allowed-extensions", ".py", ".js", ".ts", ".json", ".md", ".txt"
      ],
      "cwd": "/absolute/path/to/your/project/filesystem_server"
    }
  }
}
```

### Файл конфигурации

```json
{
  "allowed_dirs": [
    "C:/Users/YourUsername/Documents/projects",
    "D:/projects",
    "D:/Webs"
  ],
  "allowed_extensions": [
    ".py", ".js", ".ts", ".json", ".md", ".txt",
    ".yml", ".yaml", ".toml", ".cfg", ".ini", ".cs",
    ".css", ".scss", ".htm", ".html", ".xml", ".xaml"
  ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `init` | Проверяет доступность настроенных директорий и может дополнительно отобразить содержимое директории и/или прочитать... |
| `list_directory` | Отображает файлы и поддиректории в указанной директории с опциональным отчётом о прогрессе |
| `read_file` | Читает содержимое указанного файла как текст |
| `read_file_binary` | Читает содержимое указанного файла как бинарные данные в кодировке base64 |
| `list_resources` | Отображает все ресурсы (файлы и директории) в директории в формате MCP ресурсов |
| `get_resource` | Получает метаданные и действия для конкретного файла или директории |

## Возможности

- Навигация по директориям с ограничениями безопасности
- Чтение файлов только с разрешёнными расширениями
- Валидация директорий и проверка доступности
- Гибридная конфигурация (командная строка + резервный config.json)
- Поддержка отладки Visual Studio 2022 с запуском без аргументов
- Кросс-платформенная поддержка путей (разделители Windows и Unix)
- Ограничения безопасности для явно указанных директорий и типов файлов
- Отчёт о прогрессе для операций с большими директориями
- Чтение бинарных файлов с кодированием base64
- Совместимость с форматом ресурсов MCP

## Примеры использования

```
List the contents of my project directory
```

```
Read the contents of this Python file
```

```
Show me all files in my web development folder
```

```
Validate that my configured directories are accessible
```

```
Get metadata for this specific file
```

## Ресурсы

- [GitHub Repository](https://github.com/Oncorporation/filesystem_server)

## Примечания

Требует Python 3.10+. Оптимизирован для рабочих процессов Visual Studio 2022 и локальной разработки. Поддерживает три подхода к конфигурации: файл config.json (самый простой), аргументы командной строки (продвинутый) или гибридный подход. Сервер автоматически сначала использует аргументы командной строки, а затем переключается на config.json, если аргументы не предоставлены.