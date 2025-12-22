---
title: GitHub Repos Manager MCP сервер
description: Комплексный MCP сервер для взаимодействия с репозиториями GitHub через персональный токен доступа, предоставляющий 89 инструментов для управления репозиториями, отслеживания задач и совместной работы без необходимости использования Docker.
tags:
- DevOps
- Code
- Productivity
- Integration
- API
author: kurdin
featured: false
---

Комплексный MCP сервер для взаимодействия с репозиториями GitHub через персональный токен доступа, предоставляющий 89 инструментов для управления репозиториями, отслеживания задач и совместной работы без необходимости использования Docker.

## Установка

### NPX

```bash
npx -y github-repos-manager-mcp
```

### Из исходников

```bash
git clone https://github.com/kurdin/github-repos-manager.git
cd github-repos-manager
npm install
```

## Конфигурация

### Claude Desktop (NPX - macOS/Linux)

```json
{
  "mcpServers": {
    "github-repos-manager": {
      "command": "npx",
      "args": [
        "-y",
        "github-repos-manager-mcp"
      ],
      "env": {
        "GH_TOKEN": "ghp_YOUR_ACTUAL_TOKEN_HERE"
      }
    }
  }
}
```

### Claude Desktop (NPX - Windows)

```json
{
  "mcpServers": {
    "github-repos-manager": {
      "command": "npx.cmd",
      "args": [
        "-y",
        "github-repos-manager-mcp"
      ],
      "env": {
        "GH_TOKEN": "ghp_YOUR_ACTUAL_TOKEN_HERE"
      }
    }
  }
}
```

### Claude Desktop (Локальная установка)

```json
{
  "mcpServers": {
    "github-repos-manager": {
      "command": "node",
      "args": ["/full/path/to/your/project/github-repos-manager-mcp/server.cjs"],
      "env": {
        "GH_TOKEN": "ghp_YOUR_ACTUAL_TOKEN_HERE"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_pull_request` | Создание нового pull request с указанием заголовка, описания и веток |
| `edit_pull_request` | Обновление существующего pull request: заголовка, описания, статуса или базовой ветки |
| `get_pr_details` | Получение подробной информации о pull request, включая статус |
| `set_default_repo` | Установка или изменение репозитория по умолчанию для упрощения рабочих процессов |

## Возможности

- 89 мощных инструментов для полного управления рабочими процессами GitHub
- Аутентификация через токен без необходимости использования Docker
- Управление репозиториями с умным листингом и фильтрацией
- Расширенное управление задачами с поддержкой богатого контента и загрузки изображений
- Управление pull request с комплексной поддержкой жизненного цикла
- Управление ветками и коммитами с исследованием истории
- Инструменты для совместной работы и управления пользователями
- Тонкая настройка контроля доступа с разрешенными репозиториями и управлением инструментами
- Настройка репозитория по умолчанию для упрощения рабочих процессов
- Встроенная обработка лимитов GitHub API

## Переменные окружения

### Обязательные
- `GH_TOKEN` - Персональный токен доступа GitHub для аутентификации API

### Опциональные
- `GH_DEFAULT_OWNER` - Владелец репозитория по умолчанию для упрощения рабочих процессов
- `GH_DEFAULT_REPO` - Название репозитория по умолчанию для упрощения рабочих процессов
- `GH_ALLOWED_REPOS` - Список разрешенных репозиториев через запятую (owner/repo или owner)
- `GH_DISABLED_TOOLS` - Список отключенных инструментов через запятую
- `GH_ALLOWED_TOOLS` - Список разрешенных инструментов через запятую (имеет приоритет над отключенными инструментами)

## Примеры использования

```
List issues for microsoft/vscode
```

```
Create a new issue with title and description
```

```
Set default repository to microsoft/vscode
```

```
List all branches with protection status
```

```
Upload and embed images directly in issues
```

## Ресурсы

- [GitHub Repository](https://github.com/kurdin/github-repos-manager-mcp)

## Примечания

Требуется Node.js версии 18 или выше. Персональный токен доступа GitHub должен иметь права доступа 'repo', 'user:read' или 'user:email', и 'read:org'. Сервер предоставляет комплексное управление рабочими процессами GitHub с 89 инструментами и поддерживает тонкую настройку контроля доступа для безопасности.