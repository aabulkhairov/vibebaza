---
title: KYC-mcp-server MCP сервер
description: Комплексная система диагностики и мониторинга MCP сервер, предоставляющий
  детальную информацию о железе, метрики производительности и рекомендации по оптимизации
  с поддержкой AI для Windows, macOS и Linux систем.
tags:
- Monitoring
- DevOps
- Analytics
- AI
- Productivity
author: vishnurudra-ai
featured: false
---

Комплексная система диагностики и мониторинга MCP сервер, предоставляющий детальную информацию о железе, метрики производительности и рекомендации по оптимизации с поддержкой AI для Windows, macOS и Linux систем.

## Установка

### Из исходников

```bash
git clone https://github.com/yourusername/system-diagnostics-mcp.git
cd system-diagnostics-mcp
python -m venv venv
venv\Scripts\activate  # Windows
source venv/bin/activate  # macOS/Linux
pip install -r requirements.txt
```

### Дополнительная настройка для Windows

```bash
pip install wmi pywin32
```

## Конфигурация

### Claude Desktop - Windows

```json
{
  "mcpServers": {
    "system-diagnostics": {
      "command": "C:\\path\\to\\venv\\Scripts\\python.exe",
      "args": ["-m", "system_diagnostics_mcp.server"],
      "cwd": "C:\\path\\to\\system-diagnostics-mcp",
      "env": {
        "PYTHONPATH": "C:\\path\\to\\system-diagnostics-mcp"
      }
    }
  }
}
```

### Claude Desktop - macOS

```json
{
  "mcpServers": {
    "system-diagnostics": {
      "command": "/path/to/venv/bin/python",
      "args": ["-m", "system_diagnostics_mcp.server"],
      "cwd": "/path/to/system-diagnostics-mcp",
      "env": {
        "PYTHONPATH": "/path/to/system-diagnostics-mcp"
      }
    }
  }
}
```

### Claude Desktop - Linux

```json
{
  "mcpServers": {
    "system-diagnostics": {
      "command": "/path/to/venv/bin/python",
      "args": ["-m", "system_diagnostics_mcp.server"],
      "cwd": "/path/to/system-diagnostics-mcp",
      "env": {
        "PYTHONPATH": "/path/to/system-diagnostics-mcp"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_system_info` | Комплексная информация о системе |
| `get_computer_model` | Производитель, модель компьютера и детали системы |
| `get_motherboard_details` | Спецификации материнской платы, информация о BIOS и слоты памяти |
| `get_cpu_metrics` | Детальные метрики CPU и температура |
| `get_memory_metrics` | Использование памяти и топ потребителей |
| `get_storage_metrics` | Устройства хранения и их использование |
| `get_network_metrics` | Сетевые интерфейсы и подключения |
| `get_processes` | Информация о запущенных процессах |
| `get_installed_applications` | Список установленных приложений |
| `get_battery_status` | Информация о батарее и питании |
| `get_system_logs` | Последние системные логи и события |
| `diagnose_performance` | Анализ производительности и узких мест |
| `get_hardware_recommendations` | Рекомендации по обновлению железа |

## Возможности

- Информация о системе: определение ОС, характеристики железа, время работы
- Определение модели компьютера: производитель, модель, системные спецификации
- Детали материнской платы: информация о материнской плате, BIOS/UEFI, слоты памяти, возможности железа
- Метрики CPU: использование, частота, температура, статистика по ядрам
- Мониторинг памяти: использование RAM/swap, потребление памяти процессами
- Анализ хранилища: использование диска, статистика I/O, определение SSD/HDD
- Мониторинг сети: статистика интерфейсов, активные подключения, анализ трафика
- Управление процессами: запущенные процессы, потребление ресурсов
- Инвентаризация приложений: список установленных приложений
- Статус батареи: потребление энергии, здоровье батареи (ноутбуки)

## Переменные окружения

### Обязательные
- `PYTHONPATH` - Путь к директории system-diagnostics-mcp для разрешения модулей

## Примеры использования

```
Какой текущий статус моей системы?
```

```
Покажи использование CPU и памяти
```

```
Сколько места на диске у меня осталось?
```

```
Моя система работает медленно, можешь продиагностировать почему?
```

```
Какие приложения используют больше всего памяти?
```

## Ресурсы

- [GitHub Repository](https://github.com/vishnurudra-ai/KYC-mcp-server)

## Примечания

Требует Python 3.8+ и pip. Некоторые функции могут требовать повышенных прав (Запуск от имени администратора на Windows, полный доступ к диску на macOS, доступ sudo на Linux). Сервер предоставляет доступ только для чтения к системной информации без сбора чувствительных данных. URL репозитория отличается от URL установки - актуальный репозиторий находится по адресу https://github.com/vishnurudra-ai/KYC-mcp-server.