---
title: Email MCP сервер
description: MCP сервер, который предоставляет функциональность электронной почты, позволяя LLM составлять и отправлять письма через различных провайдеров (Gmail, Outlook, Yahoo и др.) с поддержкой вложений и возможностями поиска файлов.
tags:
- Messaging
- Productivity
- Integration
- API
author: Community
featured: false
---

MCP сервер, который предоставляет функциональность электронной почты, позволяя LLM составлять и отправлять письма через различных провайдеров (Gmail, Outlook, Yahoo и др.) с поддержкой вложений и возможностями поиска файлов.

## Установка

### Pip

```bash
pip install pydantic python-dotenv
```

### Запуск сервера

```bash
python -m mcp_email_server (--dir /path/to/attachment/directory)
```

## Конфигурация

### Claude Desktop - Conda

```json
{
  "mcpServers": {
    "email": {
      "command": "D:\\conda\\envs\\mcp\\python.exe",
      "args": [
        "C:\\Users\\YourUserName\\Desktop\\servers\\src\\email\\src\\mcp_server_email",
        "--dir",
        "C:\\Users\\YourUserName\\Desktop"
      ],
      "env": {
        "SENDER": "2593666979q@gmail.com",
        "PASSWORD": "tuogk......."
      }
    }
  }
}
```

### Claude Desktop - UV

```json
{
  "mcpServers": {
    "email": {
      "command": "uv",
      "args": [
        "~\\servers\\src\\email\\src\\mcp_server_email",
        "--dir",
        "C:\\Users\\YourUserName\\Desktop"
      ],
      "env": {
        "SENDER": "2593666979q@gmail.com",
        "PASSWORD": "tuogk......."
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `send_email` | Отправляет письма на основе указанной темы, содержания и получателя с поддержкой нескольких получат... |
| `search_attachments` | Ищет файлы в указанной директории, которые соответствуют заданному шаблону |

## Возможности

- Отправка писем с несколькими получателями
- Поддержка вложений в письмах
- Поиск файлов в директориях по совпадению с шаблоном
- Безопасная передача писем через SMTP
- Поддержка различных провайдеров email (Gmail, Outlook, Yahoo и др.)
- Поддержка паролей приложений для повышенной безопасности

## Переменные окружения

### Обязательные
- `SENDER` - Адрес электронной почты отправителя
- `PASSWORD` - Пароль электронной почты отправителя или пароль приложения

## Примеры использования

```
Отправить письмо нескольким получателям с PDF и изображениями в качестве вложений
```

```
Найти файлы с 'report' в имени файла для вложения
```

```
Составить и отправить тестовое письмо через MCP сервер
```

## Ресурсы

- [GitHub Repository](https://github.com/Shy2593666979/mcp-server-email)

## Примечания

Требует файл конфигурации email.json с настройками SMTP сервера. Поддерживает ограниченные типы файлов для безопасности: документы (doc, docx, pdf), архивы (zip, rar), текстовые файлы (txt, csv, json), изображения (jpg, png, gif) и другие. Для Gmail может потребоваться использование пароля приложения. Лицензирован под MIT License.