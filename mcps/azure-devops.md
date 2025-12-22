---
title: Azure DevOps MCP сервер
description: MCP сервер, который позволяет AI-ассистентам взаимодействовать с сервисами Azure DevOps, обеспечивая мост между взаимодействием на естественном языке и Azure DevOps REST API для управления рабочими элементами, проектами и командами.
tags:
- DevOps
- Integration
- Productivity
- API
author: Vortiago
featured: false
install_command: mcp install src/mcp_azure_devops/server.py --name "Azure DevOps Assistant"
---

MCP сервер, который позволяет AI-ассистентам взаимодействовать с сервисами Azure DevOps, обеспечивая мост между взаимодействием на естественном языке и Azure DevOps REST API для управления рабочими элементами, проектами и командами.

## Установка

### Из исходного кода

```bash
git clone https://github.com/Vortiago/mcp-azure-devops.git
cd mcp-azure-devops
uv pip install -e ".[dev]"
```

### PyPI

```bash
pip install mcp-azure-devops
```

## Возможности

- Запрос рабочих элементов с использованием WIQL запросов
- Получение детальной информации о рабочих элементах
- Создание рабочих элементов (задачи, баги, пользовательские истории и т.д.)
- Обновление полей и свойств рабочих элементов
- Добавление комментариев к рабочим элементам
- Просмотр истории комментариев для рабочих элементов
- Управление отношениями родитель-ребенок между рабочими элементами
- Получение проектов в организации
- Получение команд внутри организации
- Просмотр информации о членах команды

## Переменные окружения

### Обязательные
- `AZURE_DEVOPS_PAT` - Personal Access Token для доступа к Azure DevOps API
- `AZURE_DEVOPS_ORGANIZATION_URL` - Полный URL вашей организации Azure DevOps (например, https://your-organization.visualstudio.com или https://dev.azure.com/your-organisation)

## Примеры использования

```
Покажи мне все активные баги, назначенные на меня в текущем спринте
```

```
Создай пользовательскую историю в ProjectX с заголовком "Реализовать аутентификацию пользователей" и назначь её на john.doe@example.com
```

```
Измени статус бага #1234 на "Resolved" и добавь комментарий с объяснением исправления
```

```
Покажи мне всех членов команды "Core Development" в проекте "ProjectX"
```

```
Покажи все проекты в моей организации и покажи итерации для команды Development
```

## Ресурсы

- [GitHub Repository](https://github.com/Vortiago/mcp-azure-devops)

## Примечания

⚠️ ВНИМАНИЕ: Этот репозиторий больше не поддерживается. Пожалуйста, используйте официальный Microsoft Azure DevOps MCP сервер вместо него: https://github.com/microsoft/azure-devops-mcp. Официальный сервер предоставляет лучшую поддержку, постоянное обслуживание и последние возможности.