---
title: TrueNAS Core MCP сервер
description: Производственно-готовый сервер Model Context Protocol (MCP) для систем TrueNAS Core, который позволяет управлять TrueNAS хранилищем через естественный язык с помощью Claude или других MCP-совместимых клиентов.
tags:
- Storage
- DevOps
- Monitoring
- API
- Integration
author: vespo92
featured: false
---

Производственно-готовый сервер Model Context Protocol (MCP) для систем TrueNAS Core, который позволяет управлять TrueNAS хранилищем через естественный язык с помощью Claude или других MCP-совместимых клиентов.

## Установка

### uvx (Рекомендуется)

```bash
# Run directly without installation
uvx truenas-mcp-server

# Or install globally with uv
uv tool install truenas-mcp-server
```

### pip

```bash
# With pip
pip install truenas-mcp-server

# Or with pipx for isolated environment
pipx install truenas-mcp-server
```

### Из исходного кода

```bash
git clone https://github.com/vespo92/TrueNasCoreMCP.git
cd TrueNasCoreMCP
pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "truenas": {
      "command": "uvx",
      "args": ["truenas-mcp-server"],
      "env": {
        "TRUENAS_URL": "https://your-truenas-server.local",
        "TRUENAS_API_KEY": "your-api-key-here",
        "TRUENAS_VERIFY_SSL": "false"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_users` | Список всех пользователей с подробностями |
| `get_user` | Получить информацию о конкретном пользователе |
| `create_user` | Создать новую учетную запись пользователя |
| `update_user` | Изменить свойства пользователя |
| `delete_user` | Удалить учетную запись пользователя |
| `list_pools` | Показать все пулы хранения |
| `get_pool_status` | Подробное состояние пула и статистика |
| `list_datasets` | Список всех датасетов |
| `create_dataset` | Создать новый датасет с опциями |
| `update_dataset` | Изменить свойства датасета |
| `delete_dataset` | Удалить датасет |
| `list_smb_shares` | Показать SMB/CIFS шары |
| `create_smb_share` | Создать Windows шару |
| `list_nfs_exports` | Показать NFS экспорты |
| `create_nfs_export` | Создать NFS экспорт |

## Возможности

- Управление пользователями - Создание, обновление, удаление пользователей и управление правами
- Управление хранилищем - Управление пулами, датасетами, томами с полной поддержкой ZFS
- Файловые шары - Настройка SMB, NFS и iSCSI шар
- Управление снимками - Создание, удаление, откат снимков с автоматизацией
- Системный мониторинг - Проверка состояния системы, статуса пулов и использования ресурсов
- Типобезопасные операции - Полные Pydantic модели для валидации запросов/ответов
- Комплексная обработка ошибок - Подробные сообщения об ошибках и рекомендации по восстановлению
- Производственное логирование - Структурированное логирование с настраиваемыми уровнями
- Пулинг соединений - Эффективное управление HTTP соединениями с логикой повторов
- Ограничение скорости - Встроенное ограничение скорости для предотвращения злоупотребления API

## Переменные окружения

### Обязательные
- `TRUENAS_URL` - URL сервера TrueNAS
- `TRUENAS_API_KEY` - API ключ для аутентификации

### Опциональные
- `TRUENAS_VERIFY_SSL` - Проверять SSL сертификаты
- `TRUENAS_LOG_LEVEL` - Уровень логирования
- `TRUENAS_ENV` - Окружение (development/staging/production)
- `TRUENAS_HTTP_TIMEOUT` - HTTP таймаут в секундах
- `TRUENAS_ENABLE_DESTRUCTIVE_OPS` - Включить операции удаления
- `TRUENAS_ENABLE_DEBUG_TOOLS` - Включить инструменты отладки

## Примеры использования

```
List all storage pools and their health status
```

```
Create a new dataset called 'backups' in the tank pool with compression
```

```
Set up an SMB share for the documents dataset
```

```
Create a snapshot of all datasets in the tank pool
```

```
Show me users who have sudo privileges
```

## Ресурсы

- [GitHub Repository](https://github.com/vespo92/TrueNasCoreMCP)

## Примечания

Требует API ключ TrueNAS Core, который можно получить из Settings → API Keys в веб-интерфейсе TrueNAS. Сервер включает производственно-готовые функции, такие как пулинг соединений, ограничение скорости и комплексную обработку ошибок. SSL проверка может быть отключена для окружений разработки.