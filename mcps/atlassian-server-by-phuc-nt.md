---
title: Atlassian Server (by phuc-nt) MCP сервер
description: MCP сервер, который подключает AI агенты (Cline, Claude Desktop, Cursor)
  к Atlassian Jira и Confluence, позволяя им запрашивать данные и выполнять действия
  через стандартизированный интерфейс.
tags:
- Productivity
- Integration
- API
- DevOps
- CRM
author: phuc-nt
featured: false
---

MCP сервер, который подключает AI агенты (Cline, Claude Desktop, Cursor) к Atlassian Jira и Confluence, позволяя им запрашивать данные и выполнять действия через стандартизированный интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @phuc-nt/mcp-atlassian-server --client claude
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `createIssue` | Создание новых задач Jira |
| `updateIssue` | Обновление существующих задач Jira |
| `transitionIssue` | Перевод задач Jira через состояния рабочего процесса |
| `assignIssue` | Назначение задач Jira пользователям |
| `addIssueToBacklog` | Добавление задач в бэклог проекта |
| `addIssueToSprint` | Добавление задач в конкретные спринты |
| `rankIssue` | Изменение ранжирования/приоритета задач |
| `createSprint` | Создание новых спринтов в Jira |
| `startSprint` | Запуск выполнения спринта |
| `closeSprint` | Закрытие завершённых спринтов |
| `createFilter` | Создание пользовательских фильтров Jira |
| `updateFilter` | Изменение существующих фильтров Jira |
| `deleteFilter` | Удаление фильтров Jira |
| `createDashboard` | Создание новых дашбордов Jira |
| `updateDashboard` | Изменение существующих дашбордов |

## Возможности

- Подключение AI агентов к Atlassian Jira и Confluence
- Поддержка как ресурсов (только чтение), так и инструментов (действия/мутации)
- Полное управление задачами Jira (просмотр, поиск, создание, обновление, переход, назначение)
- Продвинутое управление досками и спринтами с поддержкой Agile/Scrum рабочих процессов
- Управление проектами с детальной информацией о проектах и ролях
- Управление фильтрами и дашбордами с поддержкой гаджетов
- Комплексное управление пространствами и страницами Confluence
- Управление версиями страниц и обработка вложений
- Управление комментариями для страниц Confluence
- Управление пользователями и назначение проектных ролей

## Примеры использования

```
Find all my assigned issues
```

```
Create new issue about login bug
```

## Ресурсы

- [GitHub Repository](https://github.com/phuc-nt/mcp-atlassian-server)

## Примечания

Изначально разработан и оптимизирован для использования с Cline, хотя следует стандарту MCP и работает с другими MCP-совместимыми клиентами. Использует последние Atlassian API (Jira API v3, Confluence API v2). Требует API токен с соответствующими разрешениями. См. llms-install.md для детальных инструкций по настройке, оптимизированных для AI ассистентов.