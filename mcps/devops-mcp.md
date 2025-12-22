---
title: DevOps-MCP сервер
description: Динамический Azure DevOps MCP сервер, который автоматически переключает контекст аутентификации в зависимости от текущей рабочей директории, обеспечивая бесшовную интеграцию с несколькими Azure DevOps организациями и проектами через единый MCP сервер.
tags:
- DevOps
- Integration
- Code
- Productivity
- API
author: wangkanai
featured: false
install_command: claude mcp add devops-mcp -- -y @wangkanai/devops-mcp
---

Динамический Azure DevOps MCP сервер, который автоматически переключает контекст аутентификации в зависимости от текущей рабочей директории, обеспечивая бесшовную интеграцию с несколькими Azure DevOps организациями и проектами через единый MCP сервер.

## Установка

### Claude Code (Рекомендуется)

```bash
claude mcp add devops-mcp -- -y @wangkanai/devops-mcp
```

### Глобальная установка

```bash
npm install -g @wangkanai/devops-mcp
claude mcp add devops-mcp -- devops-mcp
```

### Из исходников

```bash
git clone https://github.com/wangkanai/devops-mcp.git
cd devops-mcp
npm install
npm run build
npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "devops-mcp": {
      "command": "npx",
      "args": ["-y", "@wangkanai/devops-mcp"]
    }
  }
}
```

### Конфигурация локального репозитория

```json
{
  "organizationUrl": "https://dev.azure.com/your-org",
  "project": "YourProject",
  "pat": "your-pat-token-here",
  "description": "Azure DevOps configuration for this repository",
  "settings": {
    "timeout": 30000,
    "retries": 3,
    "apiVersion": "7.1"
  },
  "tools": {
    "workItems": true,
    "repositories": true,
    "builds": true,
    "pullRequests": true,
    "pipelines": true
  },
  "meta": {
    "configVersion": "1.0",
    "lastUpdated": "2025-07-21",
    "createdBy": "devops-mcp"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-work-items` | Получение рабочих элементов с использованием WIQL запросов или конкретных ID с выбором полей |
| `create-work-item` | Создание новых рабочих элементов с полной поддержкой иерархии (Epic → Feature → User Story → Task) |
| `update-work-item` | Обновление существующих рабочих элементов, включая состояние, назначения, родительские связи и пути итераций |
| `add-work-item-comment` | Добавление комментариев к существующим рабочим элементам для отслеживания прогресса |
| `get-repositories` | Список всех репозиториев в текущем контексте проекта |
| `get-pull-requests` | Получение pull request'ов с опциями фильтрации (статус, создатель, репозиторий) |
| `get-builds` | Получение определений сборки и недавней истории сборок с фильтрацией |
| `trigger-pipeline` | Запуск pipeline'ов сборки с параметрами и выбором ветки |
| `get-pipeline-status` | Получение детального статуса сборки и информации о временной шкале |
| `get-current-context` | Получение текущего контекста Azure DevOps на основе директории |

## Возможности

- Файлы локальной конфигурации: Каждый репозиторий содержит .azure-devops.json конфигурацию
- Динамическое переключение окружений: Автоматическое определение контекста проекта на основе расположения директории
- Поддержка множественных проектов: Поддерживает неограниченное количество проектов с отдельной аутентификацией
- Комплексная интеграция с Azure DevOps: Рабочие элементы, репозитории, сборки и многое другое
- Переключение без конфигурации: Бесшовное переключение между проектами с локальными конфигурационными файлами
- Безопасное хранение токенов: PAT токены хранятся локально для каждого репозитория (исключены из git)
- Обработка ошибок и откат: Надежная обработка ошибок с graceful degradation
- Иерархические рабочие элементы: Полная поддержка иерархии Epic → Feature → User Story → Task
- Родительские связи: Установка отношений родитель-ребенок при создании рабочих элементов
- WIQL запросы: Мощная поддержка Work Item Query Language для сложных поисков

## Примеры использования

```
Get current Azure DevOps context for this repository
```

```
Show me all active work items in this project
```

```
Create a new task for implementing authentication system
```

```
List all repositories in the current project
```

```
Get status of recent builds
```

## Ресурсы

- [GitHub Repository](https://github.com/wangkanai/devops-mcp)

## Примечания

Требуются персональные токены доступа (PAT) для аутентификации с правами доступа: Work Items (Read & Write), Code (Read), Build (Read), Project and Team (Read). Каждый репозиторий нуждается в .azure-devops.json конфигурационном файле, который следует добавить в .gitignore для безопасности. Сервер интеллектуально определяет контекст проекта на основе расположения директории для бесшовной поддержки множественных проектов.