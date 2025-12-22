---
title: Cronlytic MCP сервер
description: Комплексный сервер Model Context Protocol (MCP), который интегрируется с Cronlytic API для обеспечения удобного управления cron задачами через LLM приложения, такие как Claude Desktop.
tags:
- DevOps
- Monitoring
- API
- Productivity
- Cloud
author: Community
featured: false
---

Комплексный сервер Model Context Protocol (MCP), который интегрируется с Cronlytic API для обеспечения удобного управления cron задачами через LLM приложения, такие как Claude Desktop.

## Установка

### Быстрая настройка (Рекомендуется)

```bash
git clone https://github.com/Cronlytic/cronlytic-mcp-server.git
cd cronlytic-mcp-server
./setup_dev_env.sh
source venv/bin/activate
```

### Ручная настройка

```bash
git clone https://github.com/Cronlytic/cronlytic-mcp-server.git
cd cronlytic-mcp-server
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
pip install -e .
```

### Запуск сервера

```bash
python -m cronlytic_mcp_server.server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "cronlytic": {
      "command": "python",
      "args": ["-m", "cronlytic_mcp_server.server"],
      "env": {
        "CRONLYTIC_API_KEY": "your_api_key_here",
        "CRONLYTIC_USER_ID": "your_user_id_here"
      }
    }
  }
}
```

### Claude Desktop (Виртуальное окружение)

```json
{
  "mcpServers": {
          "cronlytic": {
        "command": "python",
        "args": ["-m", "src.server"],
        "cwd": "PATH/cronlytic-mcp-server",
        "env": {
          "VIRTUAL_ENV": "PATH/cronlytic-mcp-server/.venv",
          "PATH": "PATH/cronlytic-mcp-server/.venv/bin:${PATH}",
          "CRONLYTIC_API_KEY": "your_api_key_here",
          "CRONLYTIC_USER_ID": "your_user_id_here"
        }
      }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `health_check` | Тестирует подключение и аутентификацию с Cronlytic API, включая подключение к API, аутентифика... |

## Возможности

- Проверка состояния: Тестирование подключения и аутентификации с Cronlytic API
- Управление задачами: Создание, чтение, обновление и удаление cron задач
- Контроль задач: Приостановка, возобновление и мониторинг выполнения задач
- Логи и мониторинг: Доступ к логам выполнения и метрикам производительности
- Умные подсказки: 18 комплексных подсказок для направляемой помощи
- Ресурсы: Динамические ресурсы задач и шаблоны cron
- Производительность: Встроенный мониторинг и оптимизация
- Комплексная обработка ошибок с понятными инструкциями
- Структурированное логирование на нескольких уровнях
- Поддержка мультиплатформенного деплоя

## Переменные окружения

### Обязательные
- `CRONLYTIC_API_KEY` - Ваш Cronlytic API ключ для аутентификации
- `CRONLYTIC_USER_ID` - Ваш Cronlytic пользовательский ID для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/Cronlytic/cronlytic-mcp-server)

## Примечания

Это готовый к продакшену MCP сервер со всеми 6 завершенными фазами разработки (88/88 тестов проходят). Требует аккаунт Cronlytic с доступом к API. Сервер включает комплексную обработку ошибок, автоматические повторы с экспоненциальной задержкой для ограничения скорости и поддерживает несколько методов конфигурации (переменные окружения, конфигурационные файлы или аргументы командной строки). API ключи можно получить в панели управления Cronlytic в разделе API Keys.