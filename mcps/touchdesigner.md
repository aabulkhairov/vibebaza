---
title: TouchDesigner MCP сервер
description: MCP сервер, который позволяет AI агентам управлять и контролировать проекты TouchDesigner через создание, изменение и удаление нодов, запросы свойств и выполнение Python скриптов.
tags:
- Media
- API
- Integration
- Code
- Analytics
author: 8beeeaaat
featured: true
---

MCP сервер, который позволяет AI агентам управлять и контролировать проекты TouchDesigner через создание, изменение и удаление нодов, запросы свойств и выполнение Python скриптов.

## Установка

### MCP Bundle (Рекомендуется)

```bash
Double-click the touchdesigner-mcp.mcpb file to install the bundle in Claude Desktop
```

### NPX

```bash
npx -y touchdesigner-mcp-server@latest --stdio
```

### Docker

```bash
git clone https://github.com/8beeeaaat/touchdesigner-mcp.git
cd touchdesigner-mcp
make build
docker-compose up -d
```

## Конфигурация

### Claude Desktop - NPX

```json
{
  "mcpServers": {
    "touchdesigner": {
      "command": "npx",
      "args": ["-y", "touchdesigner-mcp-server@latest", "--stdio"]
    }
  }
}
```

### Claude Desktop - NPX с кастомным хостом/портом

```json
{
  "mcpServers": {
    "touchdesigner": {
      "command": "npx",
      "args": [
        "-y",
        "touchdesigner-mcp-server@latest",
        "--stdio",
        "--host=http://custom_host",
        "--port=9982"
      ]
    }
  }
}
```

### Claude Desktop - Docker

```json
{
  "mcpServers": {
    "touchdesigner": {
      "command": "docker",
      "args": [
        "compose",
        "-f",
        "/path/to/your/touchdesigner-mcp/docker-compose.yml",
        "exec",
        "-i",
        "touchdesigner-mcp-server",
        "node",
        "dist/cli.js",
        "--stdio",
        "--host=http://host.docker.internal"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_td_node` | Создает новый нод |
| `delete_td_node` | Удаляет существующий нод |
| `exec_node_method` | Вызывает Python метод на ноде |
| `execute_python_script` | Выполняет произвольный Python скрипт в TouchDesigner |
| `get_td_class_details` | Получает детали Python класса или модуля TouchDesigner |
| `get_td_classes` | Получает список Python классов TouchDesigner |
| `get_td_info` | Получает информацию об окружении TouchDesigner сервера |
| `get_td_node_parameters` | Получает параметры конкретного нода |
| `get_td_nodes` | Получает ноды под родительским путем с опциональной фильтрацией |
| `update_td_node_parameters` | Обновляет параметры конкретного нода |

## Возможности

- Создание, изменение и удаление TouchDesigner нодов
- Запрос свойств нодов и структуры проекта
- Программное выполнение Python скриптов в TouchDesigner
- Поиск нодов по имени, семейству или типу
- Соединение нодов внутри TouchDesigner
- Проверка ошибок на нодах и их дочерних элементах
- Мост между AI моделями и TouchDesigner WebServer DAT

## Примеры использования

```
Search for nodes and retrieve information
```

```
Connect nodes within TouchDesigner
```

```
Check for errors on nodes
```

```
Create and modify TouchDesigner projects
```

## Ресурсы

- [GitHub Repository](https://github.com/8beeeaaat/touchdesigner-mcp)

## Примечания

Требует импорта TouchDesigner компонентов: скачайте touchdesigner-mcp-td.zip, импортируйте mcp_webserver_base.tox в ваш проект по пути /project1/mcp_webserver_base. Структура каталогов должна быть сохранена точно как в извлеченном архиве для правильной загрузки модулей.