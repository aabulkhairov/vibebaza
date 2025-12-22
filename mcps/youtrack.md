---
title: YouTrack MCP сервер
description: Model Context Protocol (MCP) сервер, который обеспечивает бесшовную интеграцию
  с системой трекинга задач JetBrains YouTrack, позволяя AI-ассистентам управлять
  задачами, проектами, пользователями и пользовательскими полями.
tags:
- Productivity
- Integration
- API
- DevOps
- Code
author: tonyzorin
featured: false
---

Model Context Protocol (MCP) сервер, который обеспечивает бесшовную интеграцию с системой трекинга задач JetBrains YouTrack, позволяя AI-ассистентам управлять задачами, проектами, пользователями и пользовательскими полями.

## Установка

### Docker (Docker Hub)

```bash
docker run --rm \
  -e YOUTRACK_URL="https://your-instance.youtrack.cloud" \
  -e YOUTRACK_API_TOKEN="your-token" \
  tonyzorin/youtrack-mcp:latest
```

### Docker (GitHub Container Registry)

```bash
docker run --rm \
  -e YOUTRACK_URL="https://your-instance.youtrack.cloud" \
  -e YOUTRACK_API_TOKEN="your-token" \
  ghcr.io/tonyzorin/youtrack-mcp:latest
```

### NPM Global

```bash
npm install -g youtrack-mcp-tonyzorin
```

### NPX

```bash
npx youtrack-mcp-tonyzorin
```

### GitHub Packages NPM

```bash
npm config set @tonyzorin:registry https://npm.pkg.github.com
npm install -g @tonyzorin/youtrack-mcp
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `update_issue_state` | Обновить статус/состояние задачи, используя простые строковые значения |
| `update_issue_priority` | Обновить приоритет задачи (Critical, Major, Normal и т.д.) |
| `update_issue_assignee` | Назначить задачу пользователю, используя его логин |
| `update_issue_type` | Обновить тип задачи (Bug, Feature, Task и т.д.) |
| `update_issue_estimation` | Установить временную оценку для задачи, используя строки времени (4h, 2d, 30m, 1w) |
| `update_custom_fields` | Обновить несколько пользовательских полей одновременно с помощью пакетных операций |
| `search_issues` | Искать задачи по текстовым запросам |
| `get_project_issues` | Получить все задачи для конкретного проекта |
| `get_issue` | Получить подробную информацию о конкретной задаче |
| `create_issue` | Создать новые задачи с заголовком, описанием и назначением проекта |
| `add_dependency` | Создать связи зависимостей между задачами |
| `add_relates_link` | Создать связи отношений между задачами |
| `add_comment` | Добавить комментарии к задачам |
| `get_issue_comments` | Получить все комментарии к задаче |

## Возможности

- Управление задачами: Создание, чтение, обновление и удаление задач YouTrack
- Управление проектами: Доступ к информации о проектах и пользовательским полям
- Возможности поиска: Расширенный поиск с фильтрами и пользовательскими полями
- Управление пользователями: Получение информации о пользователях и разрешениях
- Поддержка вложений: Загрузка и обработка вложений задач (до 10MB)
- Мультиплатформенная поддержка: Поддержка архитектур ARM64/Apple Silicon и AMD64
- Полные CRUD операции с пользовательскими полями с валидацией полей
- Возможности пакетного обновления для оптимизации производительности
- Комплексная обработка ошибок с подробными сообщениями

## Переменные окружения

### Обязательные
- `YOUTRACK_URL` - URL вашего экземпляра YouTrack
- `YOUTRACK_API_TOKEN` - Ваш API токен YouTrack

### Опциональные
- `YOUTRACK_VERIFY_SSL` - Настройка проверки SSL

## Примеры использования

```
Обновить задачу DEMO-123 в статус In Progress
```

```
Установить приоритет PROJECT-456 как Critical
```

```
Назначить TASK-789 пользователю john.doe
```

```
Создать новый баг-репорт в проекте DEMO
```

```
Найти задачи, содержащие 'login bug'
```

## Ресурсы

- [GitHub Repository](https://github.com/tonyzorin/youtrack-mcp)

## Примечания

Сервер предоставляет проверенные рабочие форматы для обычных операций с четкими примерами того, что работает, а что нет. Включает полные примеры рабочих процессов для сортировки багов, разработки функций и выполнения задач. Последняя версия 1.11.1 включает комплексное управление пользовательскими полями с 567 тестами и обширным покрытием. Доступна в нескольких реестрах (Docker Hub, GitHub Container Registry, npmjs.org, GitHub Packages) с различными вариантами тегов, включая последние стабильные и рабочие сборки.