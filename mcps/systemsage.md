---
title: SystemSage MCP сервер
description: Мощный кроссплатформенный инструмент для управления и мониторинга системы, который предоставляет комплексную аналитику и возможности управления системой через Model Context Protocol (MCP).
tags:
- Monitoring
- DevOps
- Security
- Cloud
- Productivity
author: Community
featured: false
---

Мощный кроссплатформенный инструмент для управления и мониторинга системы, который предоставляет комплексную аналитику и возможности управления системой через Model Context Protocol (MCP).

## Установка

### pip

```bash
pip install systemsage
```

### pip с облачными возможностями

```bash
pip install systemsage[cloud]
```

### uv

```bash
pip install uv
uv pip install systemsage
```

## Конфигурация

### Cursor Desktop (uvx)

```json
{
    "mcpServers": {
        "systemsage": {
            "command": "uvx",
            "args": [ "systemsage@latest" ]
        }
    }
}
```

### Cursor Desktop (python)

```json
{
    "mcpServers": {
        "systemsage": {
            "command": "python",
            "args": ["-m", "SystemSage"]
        }
    }
}
```

### Cursor Desktop (отладка)

```json
{
    "mcpServers": {
        "systemsage": {
            "command": "uv",
            "args": [
                "--directory",
                "/Path to project/SystemSage/",
                "run",
                "systemsage"
            ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_cpu_usage` | Получить текущий процент использования CPU |
| `get_memory_usage` | Получить статистику использования памяти |
| `get_disk_usage` | Получить статистику использования диска |
| `get_network_interfaces` | Получить детальную информацию о сетевых интерфейсах |
| `monitor_system_resources` | Мониторинг системных ресурсов в режиме реального времени |
| `get_process_details` | Получить детальную информацию о процессе |
| `find_processes_by_name` | Найти процессы по шаблону имени |
| `get_system_alerts` | Проверить системные оповещения и проблемы |
| `cleanup_temp_files` | Очистить временные файлы |
| `get_security_status` | Проверить статус безопасности системы |
| `get_startup_programs` | Список программ, запускающихся с системой |
| `check_disk_health` | Проверить здоровье диска и SMART статус |
| `get_environment_variables` | Получить переменные окружения системы |
| `system_health_check` | Комплексная проверка здоровья системы |
| `manage_docker_containers` | Управление Docker контейнерами |

## Возможности

- Мониторинг системных ресурсов в реальном времени (CPU, память, диск)
- Управление процессами и сервисами на разных операционных системах
- Отслеживание сетевых интерфейсов и производительности
- Мониторинг Docker контейнеров и Kubernetes кластеров
- Получение мгновенных системных оповещений и диагностики
- Выполнение проверок безопасности и мониторинга
- Эффективное управление системными сервисами
- Запуск/Остановка/Перезапуск системных сервисов
- Проверки статуса безопасности системы
- Мониторинг неудачных попыток входа

## Примеры использования

```
which services is taking high resources
```

```
can you close this [service name]
```

```
can u check internet is working
```

## Ресурсы

- [GitHub Repository](https://github.com/Tarusharma1/SystemSage)

## Примечания

SystemSage - это мощный инструмент, который предоставляет обширный контроль над вашей системой. Используйте с осторожностью, так как многие инструменты могут вносить значительные изменения в вашу систему, такие как завершение процессов, управление сервисами или изменение файлов. Некоторые функции требуют прав администратора. Этот инструмент предоставляется "как есть" без каких-либо гарантий.