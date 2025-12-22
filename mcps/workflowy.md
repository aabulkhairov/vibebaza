---
title: Workflowy MCP сервер
description: Model Context Protocol (MCP) сервер для взаимодействия с Workflowy, позволяющий AI-помощникам читать и управлять вашими списками Workflowy программно.
tags:
- Productivity
- Integration
- API
author: danield137
featured: false
---

Model Context Protocol (MCP) сервер для взаимодействия с Workflowy, позволяющий AI-помощникам читать и управлять вашими списками Workflowy программно.

## Установка

### NPM Global

```bash
npm install -g mcp-workflowy
```

### NPX

```bash
npx mcp-workflowy server start
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_nodes` | Получить список узлов из вашего Workflowy (корневые узлы или дочерние элементы указанного узла) |
| `search_nodes` | Поиск узлов по тексту запроса |
| `create_node` | Создать новый узел в вашем Workflowy |
| `update_node` | Изменить текст или описание существующего узла |
| `toggle_complete` | Отметить узел как выполненный или невыполненный |

## Возможности

- Интеграция с Workflowy с аутентификацией по имени пользователя/паролю
- Полная совместимость с MCP
- Поиск, создание, обновление и отметка узлов как выполненных/невыполненных в Workflowy

## Переменные окружения

### Обязательные
- `WORKFLOWY_USERNAME` - Имя пользователя вашего аккаунта Workflowy
- `WORKFLOWY_PASSWORD` - Пароль вашего аккаунта Workflowy

## Примеры использования

```
Show my all my notes on project XYZ in workflowy
```

```
Review the codebase, mark all completed notes as completed
```

```
Given my milestones on workflowy for this project, suggest what my next task should be
```

## Ресурсы

- [GitHub Repository](https://github.com/danield137/mcp-workflowy)

## Примечания

Требует Node.js v18 или выше и аккаунт Workflowy. Переменные окружения можно указать через .env файл или как переменные окружения при запуске сервера.