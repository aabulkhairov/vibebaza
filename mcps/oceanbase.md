---
title: OceanBase MCP сервер
description: Сервер Model Context Protocol (MCP), который обеспечивает безопасное взаимодействие с базами данных OceanBase, позволяя AI-ассистентам просматривать таблицы, читать данные и выполнять SQL-запросы через контролируемый интерфейс.
tags:
- Database
- Analytics
- Security
- API
- Integration
author: yuanoOo
featured: false
---

Сервер Model Context Protocol (MCP), который обеспечивает безопасное взаимодействие с базами данных OceanBase, позволяя AI-ассистентам просматривать таблицы, читать данные и выполнять SQL-запросы через контролируемый интерфейс.

## Установка

### pip

```bash
pip install oceanbase-mcp-server
```

### Из исходного кода

```bash
# Установка зависимостей
pip install -r requirements.txt

# Запуск сервера
python -m oceanbase_mcp_server
```

### Настройка для разработки

```bash
# Клонирование репозитория
git clone https://github.com/yourusername/oceanbase_mcp_server.git
cd oceanbase_mcp_server

# Создание виртуального окружения
python -m venv venv
source venv/bin/activate  # или `venv\Scripts\activate` на Windows

# Установка зависимостей для разработки
pip install -r requirements-dev.txt

# Запуск тестов
pytest
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "oceanbase": {
      "command": "uv",
      "args": [
        "--directory", 
        "path/to/oceanbase_mcp_server",
        "run",
        "oceanbase_mcp_server"
      ],
      "env": {
        "OB_HOST": "localhost",
        "OB_PORT": "2881",
        "OB_USER": "your_username",
        "OB_PASSWORD": "your_password",
        "OB_DATABASE": "your_database"
      }
    }
  }
}
```

## Возможности

- Просмотр доступных таблиц OceanBase как ресурсов
- Чтение содержимого таблиц
- Выполнение SQL-запросов с корректной обработкой ошибок
- Безопасный доступ к базе данных через переменные окружения
- Комплексное логирование

## Переменные окружения

### Обязательные
- `OB_HOST` - Хост базы данных
- `OB_USER` - Имя пользователя базы данных
- `OB_PASSWORD` - Пароль базы данных
- `OB_DATABASE` - Имя базы данных

### Опциональные
- `OB_PORT` - Порт базы данных (по умолчанию 2881, если не указан)

## Ресурсы

- [GitHub Repository](https://github.com/yuanoOo/oceanbase_mcp_server)

## Примечания

Этот сервер делает акцент на лучших практиках безопасности, включая создание выделенных пользователей OceanBase с минимальными правами, никогда не используя root-учётные данные, ограничивая доступ к базе данных, включая логирование для аудита и регулярные проверки безопасности. Включает комплексную документацию по безопасности и следует принципу минимальных привилегий.