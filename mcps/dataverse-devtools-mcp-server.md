---
title: Dataverse DevTools MCP сервер
description: MCP сервер, предоставляющий готовые к использованию инструменты Dataverse для администрирования пользователей и безопасности, операций с данными, изучения метаданных и устранения неполадок для разработчиков Dynamics 365/Dataverse.
tags:
- CRM
- Database
- DevOps
- Security
- API
author: vignaesh01
featured: false
---

MCP сервер, предоставляющий готовые к использованию инструменты Dataverse для администрирования пользователей и безопасности, операций с данными, изучения метаданных и устранения неполадок для разработчиков Dynamics 365/Dataverse.

## Установка

### Глобальный .NET инструмент

```bash
dotnet tool install --global vignaesh01.dataversedevtoolsmcpserver
```

## Конфигурация

### VS Code (Глобальный инструмент)

```json
{
  "servers": {
    "dvmcp": {
      "type": "stdio",
      "command": "dataversedevtoolsmcpserver",
      "args": [
        "--environmentUrl",
        "https://yourorg.crm.dynamics.com"
      ]
    }
  }
}
```

### VS Code (Client Credentials)

```json
{
  "servers": {
    "dvmcp": {
      "type": "stdio",
      "command": "dataversedevtoolsmcpserver",
      "args": [
        "--environmentUrl",
        "https://yourorg.crm.dynamics.com",
        "--tenantId",
        "your-tenant-id",
        "--clientId",
        "your-client-id",
        "--clientSecret",
        "your-client-secret"
      ]
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "dvmcp": {
      "type": "stdio",
      "command": "dataversedevtoolsmcpserver",
      "args": [
        "--environmentUrl",
        "https://yourorg.crm.dynamics.com"
      ]
    }
  }
}
```

### Корпоративный прокси

```json
{
  "servers": {
    "dvmcp": {
      "type": "stdio",
      "command": "dataversedevtoolsmcpserver",
      "args": [
        "--environmentUrl",
        "https://yourorg.crm.dynamics.com"
      ],
      "env":{
          "HTTP_PROXY": "http://<username@domain.com>:<password>@<proxy.domain.com>:8080",
          "HTTPS_PROXY": "http://<username@domain.com>:<password>@<proxy.domain.com>:8080"
        }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `GetCurrentUser` | Получить данные текущего авторизованного пользователя |
| `GetUserById` | Получить данные пользователя по ID |
| `SearchUsersByKeyword` | Поиск пользователей, где полное имя содержит ключевое слово (с пагинацией) |
| `GetUserQueues` | Список очередей для пользователя (с пагинацией) |
| `GetUserTeams` | Список команд для пользователя (с пагинацией) |
| `GetUserRoles` | Список ролей безопасности для пользователя |
| `AssignRoleToUser` | Назначить роль пользователю |
| `RemoveRoleFromUser` | Удалить роль у пользователя |
| `ChangeUserBU` | Изменить подразделение пользователя |
| `AddUserToTeam` | Добавить пользователя в команду |
| `RemoveUserFromTeam` | Удалить пользователя из команды |
| `GetEntityPrivByRoleId` | Привилегии роли для конкретной сущности |
| `GetAllPrivByRoleId` | Все привилегии для роли |
| `ListRolesByPrivId` | Роли, имеющие конкретную привилегию по ID |
| `ExecuteFetchXml` | Выполнить FetchXML запрос (поддерживает paging-cookie) |

## Возможности

- Инструменты администрирования пользователей и безопасности
- Операции с данными через FetchXML и выполнение Web API
- Изучение метаданных сущностей с пагинацией
- Обнаружение Custom Actions и Custom APIs
- Устранение неполадок логов трассировки плагинов
- Поддержка интерактивной аутентификации или client credentials
- Поддержка корпоративного прокси
- Интеграция с VS Code, Visual Studio и Claude Desktop

## Переменные окружения

### Опциональные
- `HTTP_PROXY` - HTTP прокси сервер для корпоративных сетей
- `HTTPS_PROXY` - HTTPS прокси сервер для корпоративных сетей

## Примеры использования

```
What is my current Dataverse user and business unit?
```

```
Find the user 'Jane Doe' and show her queues and teams.
```

```
List security roles for the user Jane Doe.
```

```
Assign Basic User security role to the user Jane Doe.
```

```
Execute this FetchXML query: <paste FetchXML>.
```

## Ресурсы

- [GitHub Repository](https://github.com/vignaesh01/DataverseDevToolsMcpServer)

## Примечания

Требует .NET 8.0 SDK или новее, URL среды Dataverse и соответствующие разрешения Dataverse. Для логов трассировки плагинов необходимо включить Plugin Trace Log в среде. Поддерживает как интерактивную аутентификацию, так и аутентификацию через service principal Azure AD. Многие операции поиска поддерживают пагинацию. Обновление через 'dotnet tool update -g vignaesh01.dataversedevtoolsmcpserver' и удаление через 'dotnet tool uninstall -g vignaesh01.dataversedevtoolsmcpserver'.