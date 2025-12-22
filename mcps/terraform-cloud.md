---
title: Terraform-Cloud MCP сервер
description: MCP сервер, который интегрирует AI ассистентов с Terraform Cloud API, позволяя управлять вашей инфраструктурой через естественный разговор с полными возможностями управления workspace, проектами, запусками и состояниями.
tags:
- DevOps
- Cloud
- API
- Integration
- Productivity
author: severity1
featured: false
install_command: claude mcp add -e TFC_TOKEN=YOUR_TF_TOKEN -e ENABLE_DELETE_TOOLS=false
  -s user terraform-cloud-mcp -- "terraform-cloud-mcp"
---

MCP сервер, который интегрирует AI ассистентов с Terraform Cloud API, позволяя управлять вашей инфраструктурой через естественный разговор с полными возможностями управления workspace, проектами, запусками и состояниями.

## Установка

### Локальная установка

```bash
# Clone the repository
git clone https://github.com/severity1/terraform-cloud-mcp.git
cd terraform-cloud-mcp

# Create virtual environment and activate it
uv venv
source .venv/bin/activate

# Install package
uv pip install .
```

### Установка через Docker

```bash
# Clone the repository
git clone https://github.com/severity1/terraform-cloud-mcp.git
cd terraform-cloud-mcp

# Build the Docker image
docker build -t terraform-cloud-mcp:latest .
```

## Конфигурация

### Claude Desktop локально

```json
{
  "mcpServers": {
    "terraform-cloud-mcp": {
      "command": "/path/to/uv",
      "args": [
        "--directory",
        "/path/to/your/terraform-cloud-mcp",
        "run",
        "terraform-cloud-mcp"
      ],
      "env": {
        "TFC_TOKEN": "your_actual_token_here",
        "TFC_ADDRESS": "https://app.terraform.io",
        "ENABLE_DELETE_TOOLS": "false",
        "READ_ONLY_TOOLS": "false"
      }
    }
  }
}
```

### Claude Desktop с Docker

```json
{
  "mcpServers": {
    "terraform-cloud-mcp": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm",
        "-e", "TFC_TOKEN",
        "-e", "TFC_ADDRESS",
        "-e", "ENABLE_DELETE_TOOLS",
        "-e", "READ_ONLY_TOOLS",
        "terraform-cloud-mcp:latest"
      ],
      "env": {
        "TFC_TOKEN": "your_actual_token_here",
        "TFC_ADDRESS": "https://app.terraform.io",
        "ENABLE_DELETE_TOOLS": "false",
        "READ_ONLY_TOOLS": "false"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_account_details` | Получает информацию об аккаунте для аутентифицированного пользователя или служебного аккаунта |
| `list_workspaces` | Список и фильтрация workspace |
| `create_workspace` | Создание нового workspace с опциональными параметрами |
| `update_workspace` | Обновление конфигурации существующего workspace |
| `delete_workspace` | Удаление workspace и всего его содержимого (требует ENABLE_DELETE_TOOLS=true) |
| `lock_workspace` | Блокировка workspace для предотвращения запусков |
| `unlock_workspace` | Разблокировка workspace для разрешения запусков |
| `create_run` | Создание и постановка в очередь Terraform run в workspace |
| `list_runs_in_workspace` | Список и фильтрация запусков в определенном workspace |
| `apply_run` | Применение запуска, ожидающего подтверждения |
| `discard_run` | Отклонение запуска, ожидающего подтверждения |
| `cancel_run` | Отмена запуска, который в данный момент планируется или применяется |
| `get_plan_details` | Получение детальной информации о конкретном плане |
| `get_plan_json_output` | Получение JSON плана выполнения для конкретного плана |
| `get_apply_details` | Получение детальной информации о конкретном применении |

## Возможности

- Управление аккаунтом: получение информации об аккаунте для аутентифицированных пользователей или служебных аккаунтов
- Управление Workspace: создание, чтение, обновление, блокировка/разблокировка workspace и опциональное удаление workspace
- Управление проектами: создание, список, обновление проектов и управление привязкой тегов проектов
- Управление запусками: создание запусков, список запусков, получение деталей запуска, применение/отклонение/отмена запусков
- Управление планами: получение деталей плана и JSON вывода выполнения с продвинутой обработкой HTTP перенаправлений
- Управление применениями: получение деталей применения и восстановление после неудачных загрузок состояний
- Управление организацией: список, создание, обновление организаций, просмотр прав организации
- Оценка стоимости: получение детальных оценок стоимости изменений инфраструктуры
- Результаты оценки: получение деталей оценки работоспособности, JSON вывода, файлов схемы и логов
- Управление версиями состояний: список, получение, создание и загрузка версий состояний

## Переменные окружения

### Обязательные
- `TFC_TOKEN` - токен Terraform Cloud API

### Опциональные
- `TFC_ADDRESS` - адрес Terraform Cloud/Enterprise (по умолчанию https://app.terraform.io)
- `ENABLE_DELETE_TOOLS` - включение/выключение деструктивных операций (по умолчанию false)
- `READ_ONLY_TOOLS` - включение только операций чтения (по умолчанию false)
- `ENABLE_RAW_RESPONSE` - возврат сырых vs отфильтрованных ответов (по умолчанию false)

## Ресурсы

- [GitHub Repository](https://github.com/severity1/terraform-cloud-mcp)

## Примечания

Требует Python 3.12+, MCP (включает FastMCP и инструменты разработки), и пакетный менеджер uv. Совместим с Claude, Claude Code CLI, Claude Desktop, Cursor, Copilot Studio и другими платформами с поддержкой MCP. Включает комплексные функции безопасности с контролем деструктивных операций и режим только для чтения для продакшн окружений.