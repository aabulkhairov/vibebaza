---
title: DataWorks MCP сервер
description: MCP сервер, который предоставляет инструменты для взаимодействия ИИ с DataWorks Open API, позволяя AI агентам легко выполнять операции с облачными ресурсами через инфраструктуру Alibaba Cloud.
tags:
- Cloud
- API
- Analytics
- Integration
- DevOps
author: aliyun
featured: false
---

MCP сервер, который предоставляет инструменты для взаимодействия ИИ с DataWorks Open API, позволяя AI агентам легко выполнять операции с облачными ресурсами через инфраструктуру Alibaba Cloud.

## Установка

### NPM Global

```bash
npm install -g alibabacloud-dataworks-mcp-server
```

### NPM Local

```bash
npm install alibabacloud-dataworks-mcp-server
```

### Из исходного кода

```bash
git clone https://github.com/aliyun/alibabacloud-dataworks-mcp-server
cd alibabacloud-dataworks-mcp-server
pnpm install
pnpm run build
```

## Конфигурация

### Установка через NPM

```json
{
  "mcpServers": {
    "alibabacloud-dataworks-mcp-server": {
      "command": "npx",
      "args": ["alibabacloud-dataworks-mcp-server"],
      "env": {
        "REGION": "your_dataworks_open_api_region_id_here",
        "ALIBABA_CLOUD_ACCESS_KEY_ID": "your_alibaba_cloud_access_key_id",
        "ALIBABA_CLOUD_ACCESS_KEY_SECRET": "your_alibaba_cloud_access_key_secret",
        "TOOL_CATEGORIES": "optional_your_tool_categories_here_ex_UTILS",
        "TOOL_NAMES": "optional_your_tool_names_here_ex_ListProjects"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### Из исходного кода

```json
{
  "mcpServers": {
    "alibabacloud-dataworks-mcp-server": {
      "command": "node",
      "args": ["/path/to/alibabacloud-dataworks-mcp-server/build/index.js"],
      "env": {
        "REGION": "your_dataworks_open_api_region_id_here",
        "ALIBABA_CLOUD_ACCESS_KEY_ID": "your_alibaba_cloud_access_key_id",
        "ALIBABA_CLOUD_ACCESS_KEY_SECRET": "your_alibaba_cloud_access_key_secret",
        "TOOL_CATEGORIES": "optional_your_tool_categories_here_ex_SERVER_IDE_DEFAULT",
        "TOOL_NAMES": "optional_your_tool_names_here_ex_ListProjects"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## Возможности

- Взаимодействие с DataWorks Open API
- Управление ресурсами DataWorks
- Стандартизированные взаимодействия с облачными ресурсами для AI агентов
- Основан на Alibaba Cloud Open API

## Переменные окружения

### Обязательные
- `REGION` - ID региона DataWorks Open API
- `ALIBABA_CLOUD_ACCESS_KEY_ID` - ID ключа доступа Alibaba Cloud
- `ALIBABA_CLOUD_ACCESS_KEY_SECRET` - Секретный ключ доступа Alibaba Cloud

### Опциональные
- `TOOL_CATEGORIES` - Опциональный фильтр категорий инструментов (например, SERVER_IDE_DEFAULT)
- `TOOL_NAMES` - Опциональный фильтр имен инструментов (например, ListProjects)

## Ресурсы

- [GitHub Repository](https://github.com/aliyun/alibabacloud-dataworks-mcp-server)

## Примечания

Требует Node.js версии 16 или выше и учетные данные DataWorks Open API. Доступные инструменты можно найти на https://dataworks.data.aliyun.com/dw-pop-mcptools. Лицензирован под Apache 2.0.