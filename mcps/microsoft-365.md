---
title: Microsoft 365 MCP сервер
description: MCP сервер, который позволяет выполнять команды CLI для Microsoft 365 на естественном языке для управления различными областями Microsoft 365, включая Entra ID, OneDrive, OneNote, Outlook, Planner, Power Apps, Power Automate, SharePoint Online, Teams и многое другое.
tags:
- Productivity
- Cloud
- Integration
- API
- DevOps
author: Community
featured: false
---

MCP сервер, который позволяет выполнять команды CLI для Microsoft 365 на естественном языке для управления различными областями Microsoft 365, включая Entra ID, OneDrive, OneNote, Outlook, Planner, Power Apps, Power Automate, SharePoint Online, Teams и многое другое.

## Установка

### NPX

```bash
npx -y @pnp/cli-microsoft365-mcp-server@latest
```

### Из исходного кода

```bash
npm install
npm run build
npm run start
```

## Конфигурация

### VS Code

```json
{
    "servers": {
        "CLI for Microsoft 365 MCP Server": {
            "type": "stdio",
            "command": "npx",
            "args": [
                "-y",
                "@pnp/cli-microsoft365-mcp-server@latest"
          ]
        }
    }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "CLI-Microsoft365": {
      "command": "npx",
      "args": ["-y", "@pnp/cli-microsoft365-mcp-server@latest"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `m365GetCommands` | Получает все команды CLI для Microsoft 365 для использования Model Context Protocol при выборе правильной команды... |
| `m365GetCommandDocs` | Получает документацию для указанной команды CLI для Microsoft 365 для использования Model Context Protocol... |
| `m365RunCommand` | Выполняет указанную команду CLI для Microsoft 365 для использования Model Context Protocol при выполнении... |

## Возможности

- Выполнение команд CLI для Microsoft 365 на естественном языке
- Объединение нескольких команд для выполнения сложных запросов
- Управление сайтами, списками и контентом SharePoint Online
- Создание и управление Microsoft Teams и каналами
- Управление решениями Power Platform и потоками Power Automate
- Управление планами, корзинами и задачами Planner
- Работа с Entra ID, OneDrive, OneNote, Outlook и Viva Engage
- Поддержка сложных многошаговых операций

## Примеры использования

```
Add a new list to this site with title "awesome ducks". Then add new columns to that list including them in the default view. The first should be a text description columns and the second one should be a user column. Then add 3 items to this list with some funny jokes about docs added in the description column and adding my user in the user column. use emojis 🙂
```

```
Create a new Team on Teams with name "Awesome Ducks" and in the General channel add a welcome post
```

```
can you check if I have HoursReportingReminder flow and if so disable it
```

```
can you create a new plan in planner to manage work for the awesome ducks. I need some sample buckets and tasks to get started
```

## Ресурсы

- [GitHub Repository](https://github.com/pnp/cli-microsoft365-mcp-server)

## Примечания

Требует Node.js версии 20.x или выше и глобально установленный CLI для Microsoft 365 (npm i -g @pnp/cli-microsoft365). Первоначальная настройка требует аутентификации через m365 login и конфигурации со специфическими настройками CLI. Лучше всего работает с Claude Sonnet 4 или Claude Sonnet 3.7. Сервер использует существующий контекст аутентификации CLI для Microsoft 365.