---
title: GitHub Actions MCP сервер
description: MCP сервер для GitHub Actions API, позволяющий AI-ассистентам управлять и работать с workflow GitHub Actions, включая запуск, мониторинг и анализ выполнения workflow.
tags:
- DevOps
- API
- Code
- Integration
- Productivity
author: ko1ynnky
featured: false
---

MCP сервер для GitHub Actions API, позволяющий AI-ассистентам управлять и работать с workflow GitHub Actions, включая запуск, мониторинг и анализ выполнения workflow.

## Установка

### Из исходников (Unix/Linux/macOS)

```bash
git clone https://github.com/ko1ynnky/github-actions-mcp-server.git
cd github-actions-mcp-server
npm install
npm run build
```

### Из исходников (Windows)

```bash
git clone https://github.com/ko1ynnky/github-actions-mcp-server.git
cd github-actions-mcp-server
npm install
npm run build:win
```

### Batch файл для Windows

```bash
run-server.bat [optional-github-token]
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "github-actions": {
      "command": "node",
      "args": [
        "<path-to-mcp-server>/dist/index.js"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

### Codeium

```json
{
  "mcpServers": {
    "github-actions": {
      "command": "node",
      "args": [
        "<path-to-mcp-server>/dist/index.js"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

### Windsurf

```json
{
  "mcpServers": {
    "github-actions": {
      "command": "node",
      "args": [
        "<path-to-mcp-server>/dist/index.js"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_workflows` | Список workflow в GitHub репозитории с поддержкой пагинации |
| `get_workflow` | Получение деталей конкретного workflow по ID или имени файла |
| `get_workflow_usage` | Получение статистики использования workflow, включая оплачиваемые минуты |
| `list_workflow_runs` | Список всех запусков workflow для репозитория или конкретного workflow с возможностью фильтрации |
| `get_workflow_run` | Получение деталей конкретного запуска workflow |
| `get_workflow_run_jobs` | Получение задач для конкретного запуска workflow с фильтрацией и пагинацией |
| `trigger_workflow` | Запуск workflow с опциональными входными параметрами |
| `cancel_workflow_run` | Отмена выполняющегося workflow |
| `rerun_workflow` | Повторный запуск workflow |

## Возможности

- Полное управление Workflow: Просмотр списка, просмотр, запуск, отмена и повторный запуск workflow
- Анализ запусков Workflow: Получение подробной информации о запусках workflow и их задачах
- Комплексная обработка ошибок: Четкие сообщения об ошибках с расширенными деталями
- Гибкая валидация типов: Надежная проверка типов с корректной обработкой вариаций API
- Дизайн с фокусом на безопасность: Обработка таймаутов, ограничение скорости и строгая валидация URL

## Переменные окружения

### Обязательные
- `GITHUB_PERSONAL_ACCESS_TOKEN` - GitHub Personal Access Token для аутентификации в API

## Примеры использования

```
Просмотр списка workflow в вашем репозитории
```

```
Запуск workflow с конкретными входными данными и ссылкой на ветку
```

```
Мониторинг запусков workflow и получение подробной информации о задачах
```

```
Отмена выполняющихся workflow или повторный запуск провалившихся workflow
```

## Ресурсы

- [GitHub Repository](https://github.com/ko1ynnky/github-actions-mcp-server)

## Примечания

⚠️ Уведомление об архивации: Этот репозиторий скоро будет заархивирован, так как официальный GitHub MCP сервер добавляет поддержку Actions. Совместим с Claude Desktop, Codeium и Windsurf. Включает batch файлы и команды сборки специально для Windows.