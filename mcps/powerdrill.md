---
title: Powerdrill MCP сервер
description: MCP сервер, который предоставляет инструменты для взаимодействия с
  датасетами Powerdrill, позволяя анализировать данные и выполнять запросы с помощью
  вопросов на естественном языке.
tags:
- Analytics
- Database
- AI
- API
author: Community
featured: false
---

MCP сервер, который предоставляет инструменты для взаимодействия с датасетами Powerdrill, позволяя анализировать данные и выполнять запросы с помощью вопросов на естественном языке.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @powerdrillai/powerdrill-mcp --client claude
```

### NPM Global

```bash
npm install -g @powerdrillai/powerdrill-mcp
```

### NPX

```bash
npx @powerdrillai/powerdrill-mcp
```

### Из исходного кода

```bash
git clone https://github.com/yourusername/powerdrill-mcp.git
cd powerdrill-mcp
npm install
```

### Скрипт установки

```bash
chmod +x setup.sh
./setup.sh
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "powerdrill": {
    "command": "npx",
    "args": [
      "-y",
      "@powerdrillai/powerdrill-mcp@latest"
    ],
    "env": {
      "POWERDRILL_USER_ID": "your_actual_user_id",
      "POWERDRILL_PROJECT_API_KEY": "your_actual_project_api_key"
    }
  }
}
```

### Claude Desktop (Node)

```json
{
  "powerdrill": {
    "command": "node",
    "args": ["/path/to/powerdrill-mcp/dist/index.js"],
    "env": {
      "POWERDRILL_USER_ID": "your_actual_user_id",
      "POWERDRILL_PROJECT_API_KEY": "your_actual_project_api_key"
    }
  }
}
```

### Cursor (NPX)

```json
{
  "powerdrill": {
    "command": "npx",
    "args": [
      "-y",
      "@powerdrillai/powerdrill-mcp@latest"
    ],
    "env": {
      "POWERDRILL_USER_ID": "your_actual_user_id",
      "POWERDRILL_PROJECT_API_KEY": "your_actual_project_api_key"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `mcp_powerdrill_list_datasets` | Выводит список доступных датасетов из вашего аккаунта Powerdrill |
| `mcp_powerdrill_get_dataset_overview` | Получает детальную информацию о конкретном датасете |
| `mcp_powerdrill_create_job` | Создает задачу для анализа данных с помощью вопросов на естественном языке |
| `mcp_powerdrill_create_session` | Создает новую сессию для группировки связанных задач |
| `mcp_powerdrill_list_data_sources` | Выводит список источников данных в конкретном датасете |
| `mcp_powerdrill_list_sessions` | Выводит список сессий из вашего аккаунта Powerdrill |
| `mcp_powerdrill_create_dataset` | Создает новый датасет в вашем аккаунте Powerdrill |
| `mcp_powerdrill_create_data_source_from_local_file` | Создает новый источник данных путем загрузки локального файла в указанный датасет |

## Возможности

- Аутентификация в Powerdrill с помощью User ID и Project API Key
- Получение списка доступных датасетов в вашем аккаунте Powerdrill
- Получение детальной информации о конкретных датасетах
- Создание и выполнение задач на датасетах с помощью вопросов на естественном языке
- Интеграция с Claude Desktop и другими MCP-совместимыми клиентами

## Переменные окружения

### Обязательные
- `POWERDRILL_USER_ID` - Ваш User ID в Powerdrill для аутентификации
- `POWERDRILL_PROJECT_API_KEY` - Ваш Project API Key в Powerdrill для аутентификации

## Примеры использования

```
Какие датасеты доступны в моем аккаунте Powerdrill?
```

```
Покажи мне все мои датасеты
```

```
Создай новый датасет под названием "Sales Analytics"
```

```
Загрузи файл /Users/your_name/Downloads/sales_data.csv в датасет {dataset_id}
```

```
Расскажи мне больше об этом датасете: {dataset_id}
```

## Ресурсы

- [GitHub Repository](https://github.com/powerdrillai/powerdrill-mcp)

## Примечания

Требуется аккаунт Powerdrill Team с действующими API-ключами. Предоставляются видеоуроки по настройке Powerdrill Team и API-ключей. Доступны несколько вариантов веб-клиентов, включая версии для Node.js и Python.