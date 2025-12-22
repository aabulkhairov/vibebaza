---
title: Atlassian MCP сервер
description: MCP сервер для продуктов Atlassian (Confluence и Jira), который поддерживает как Cloud, так и Server/Data Center развертывания с комплексными возможностями поиска, управления контентом и отслеживания задач.
tags:
- Productivity
- Integration
- API
- Cloud
- Search
author: sooperset
featured: true
---

MCP сервер для продуктов Atlassian (Confluence и Jira), который поддерживает как Cloud, так и Server/Data Center развертывания с комплексными возможностями поиска, управления контентом и отслеживания задач.

## Установка

### Docker

```bash
docker pull ghcr.io/sooperset/mcp-atlassian:latest
```

## Конфигурация

### Claude Desktop - API Token

```json
{
  "mcpServers": {
    "mcp-atlassian": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e", "CONFLUENCE_URL",
        "-e", "CONFLUENCE_USERNAME",
        "-e", "CONFLUENCE_API_TOKEN",
        "-e", "JIRA_URL",
        "-e", "JIRA_USERNAME",
        "-e", "JIRA_API_TOKEN",
        "ghcr.io/sooperset/mcp-atlassian:latest"
      ],
      "env": {
        "CONFLUENCE_URL": "https://your-company.atlassian.net/wiki",
        "CONFLUENCE_USERNAME": "your.email@company.com",
        "CONFLUENCE_API_TOKEN": "your_confluence_api_token",
        "JIRA_URL": "https://your-company.atlassian.net",
        "JIRA_USERNAME": "your.email@company.com",
        "JIRA_API_TOKEN": "your_jira_api_token"
      }
    }
  }
}
```

## Возможности

- Автоматическое обновление Jira из заметок встреч
- AI-поиск по Confluence с резюмированием
- Умная фильтрация задач Jira по проекту и дате
- Создание и управление контентом для технической документации
- Поддержка как Cloud, так и Server/Data Center развертываний
- Множественные методы аутентификации (API Token, Personal Access Token, OAuth 2.0)
- Поддержка конфигурации прокси
- Конфигурация пользовательских HTTP заголовков
- Режим только для чтения для безопасных операций

## Переменные окружения

### Обязательные
- `CONFLUENCE_URL` - URL вашего экземпляра Confluence
- `CONFLUENCE_USERNAME` - Имя пользователя для аутентификации Confluence
- `CONFLUENCE_API_TOKEN` - API токен для аутентификации Confluence
- `JIRA_URL` - URL вашего экземпляра Jira
- `JIRA_USERNAME` - Имя пользователя для аутентификации Jira
- `JIRA_API_TOKEN` - API токен для аутентификации Jira

### Опциональные
- `CONFLUENCE_SPACES_FILTER` - Фильтр по ключам пространств (например, 'DEV,TEAM,DOC')
- `JIRA_PROJECTS_FILTER` - Фильтр по ключам проектов (например, 'PROJ,DEV,SUPPORT')
- `READ_ONLY_MODE` - Установите в 'true' для отключения операций записи
- `MCP_VERBOSE` - Установите в 'true' для более подробного логирования
- `ENABLED_TOOLS` - Список названий инструментов через запятую для включения

## Примеры использования

```
Обновить Jira из наших заметок встречи
```

```
Найти наше руководство по OKR в Confluence и резюмировать его
```

```
Показать мне срочные баги в проекте PROJ за прошлую неделю
```

```
Создать техническую документацию дизайна для функции XYZ
```

## Ресурсы

- [GitHub Repository](https://github.com/sooperset/mcp-atlassian)

## Примечания

Поддерживает множественные методы аутентификации, включая OAuth 2.0 для повышенной безопасности. Включает совместимость с Confluence 6.0+ и Jira 8.14+ для Server/Data Center развертываний. Имеет комплексную поддержку прокси и конфигурацию пользовательских заголовков для корпоративных сред.