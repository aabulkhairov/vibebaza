---
title: Golang Filesystem Server MCP сервер
description: Этот MCP сервер предоставляет безопасный доступ к локальной файловой системе через Model Context Protocol, предлагая комплексные операции с файлами и директориями с валидацией путей и контролем безопасности.
tags:
- Storage
- Security
- DevOps
- Code
- Productivity
author: mark3labs
featured: true
---

Этот MCP сервер предоставляет безопасный доступ к локальной файловой системе через Model Context Protocol, предлагая комплексные операции с файлами и директориями с валидацией путей и контролем безопасности.

## Установка

### Go Install

```bash
go install github.com/mark3labs/mcp-filesystem-server@latest
```

### Standalone сервер

```bash
mcp-filesystem-server /path/to/allowed/directory [/another/allowed/directory ...]
```

### Docker

```bash
docker run -i --rm ghcr.io/mark3labs/mcp-filesystem-server:latest /path/to/allowed/directory
```

### Go библиотека

```bash
package main

import (
	"log"
	"os"

	"github.com/mark3labs/mcp-filesystem-server/filesystemserver"
)

func main() {
	// Create a new filesystem server with allowed directories
	allowedDirs := []string{"/path/to/allowed/directory", "/another/allowed/directory"}
	fs, err := filesystemserver.NewFilesystemServer(allowedDirs)
	if err != nil {
		log.Fatalf("Failed to create server: %v", err)
	}

	// Serve requests
	if err := fs.Serve(); err != nil {
		log.Fatalf("Server error: %v", err)
	}
}
```

## Конфигурация

### MCP конфигурация

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "mcp-filesystem-server",
      "args": ["/path/to/allowed/directory", "/another/allowed/directory"]
    }
  }
}
```

### Docker MCP конфигурация

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "ghcr.io/mark3labs/mcp-filesystem-server:latest",
        "/path/to/allowed/directory"
      ]
    }
  }
}
```

### Docker с монтированием тома

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "--volume=/allowed/directory/in/host:/allowed/directory/in/container",
        "ghcr.io/mark3labs/mcp-filesystem-server:latest",
        "/allowed/directory/in/container"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `read_file` | Прочитать полное содержимое файла из файловой системы |
| `read_multiple_files` | Прочитать содержимое нескольких файлов за одну операцию |
| `write_file` | Создать новый файл или перезаписать существующий файл новым содержимым |
| `copy_file` | Копировать файлы и директории |
| `move_file` | Переместить или переименовать файлы и директории |
| `delete_file` | Удалить файл или директорию из файловой системы |
| `modify_file` | Обновить файл путем поиска и замены текста с использованием строкового поиска или regex |
| `list_directory` | Получить подробный список всех файлов и директорий в указанном пути |
| `create_directory` | Создать новую директорию или убедиться, что директория существует |
| `tree` | Возвращает иерархическое JSON представление структуры директории |
| `search_files` | Рекурсивный поиск файлов и директорий, соответствующих паттерну |
| `search_within_files` | Поиск текста в содержимом файлов в деревьях директорий |
| `get_file_info` | Получить подробные метаданные о файле или директории |
| `list_allowed_directories` | Возвращает список директорий, к которым данному серверу разрешен доступ |

## Возможности

- Безопасный доступ к указанным директориям
- Валидация путей для предотвращения атак обхода директорий
- Разрешение символических ссылок с проверками безопасности
- Определение MIME типов
- Поддержка текстовых, бинарных и графических файлов
- Ограничения размера для встроенного содержимого и base64 кодирования

## Ресурсы

- [GitHub Repository](https://github.com/mark3labs/mcp-filesystem-server)

## Примечания

Этот сервер предоставляет file:// ресурсы для доступа к файлам и директориям в локальной файловой системе. Создан на Go и поддерживает настраиваемые разрешенные директории для повышенной безопасности.