---
title: BambooHR MCP сервер
description: MCP сервер, который предоставляет типизированный интерфейс для BambooHR API,
  обеспечивая доступ к данным сотрудников, отслеживанию времени, управлению проектами и HR информации.
tags:
- API
- CRM
- Productivity
- Integration
author: encoreshao
featured: false
---

MCP сервер, который предоставляет типизированный интерфейс для BambooHR API, обеспечивая доступ к данным сотрудников, отслеживанию времени, управлению проектами и HR информации.

## Установка

### Из исходного кода

```bash
# Clone the repository
git clone https://github.com/encoreshao/bamboohr-mcp.git

# Navigate to the project directory
cd bamboohr-mcp

# Install dependencies
npm install
```

## Возможности

- TypeScript типы для всех моделей и ответов API
- Простой, основанный на промисах API для всех основных эндпоинтов BambooHR
- Легко расширяется и интегрируется в ваши собственные проекты
- Доступ к справочнику сотрудников с именем, email и должностью
- Функциональность "кто сегодня отсутствует"
- Управление проектами и задачами
- Отправка и получение записей времени
- Отслеживание рабочих часов

## Переменные окружения

### Обязательные
- `BAMBOOHR_TOKEN` - Ваш токен BambooHR API
- `BAMBOOHR_COMPANY_DOMAIN` - Домен вашей компании в BambooHR (часть перед .bamboohr.com)
- `BAMBOOHR_EMPLOYEE_ID` - Ваш ID сотрудника в BambooHR

## Примеры использования

```
List all employees with name, email, and job title
```

```
Check who's out today
```

```
Submit work hours for specific projects and tasks
```

```
Fetch employee directory information
```

```
Retrieve time entries for tracking
```

## Ресурсы

- [GitHub Repository](https://github.com/encoreshao/bamboohr-mcp)

## Примечания

Чтобы создать токен BambooHR API: войдите в свою учетную запись, кликните на фото профиля, выберите 'API Keys', нажмите 'Add New Key', введите имя и скопируйте сгенерированный токен. Домен вашей компании - это поддомен в URL BambooHR, а ваш ID сотрудника можно найти в URL профиля. Библиотека включает вспомогательные функции, такие как fetchWhosOut, fetchProjects, submitWorkHours, getMe, fetchEmployeeDirectory и fetchTimeEntries.