---
title: Email SMTP MCP сервер
description: MCP сервер, который позволяет AI-ассистентам отправлять электронные письма через SMTP, поддерживает как обычные текстовые, так и HTML-письма с вложениями, функциональность CC/BCC и отправку нескольким получателям.
tags:
- Messaging
- Productivity
- Integration
- API
author: Community
featured: false
---

MCP сервер, который позволяет AI-ассистентам отправлять электронные письма через SMTP, поддерживает как обычные текстовые, так и HTML-письма с вложениями, функциональность CC/BCC и отправку нескольким получателям.

## Установка

### Из исходного кода

```bash
# Install uv (Python package manager)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Restart your terminal or run:
source ~/.bashrc

# Install project dependencies
cd email-mcp-server
uv sync
```

## Конфигурация

### Claude Desktop/Cursor

```json
{
  "mcpServers": {
      "mcp-server": {
          "command": "uv",
          "args": [
              "--directory",
              "path/to/the/app/email-mcp-server",
              "run",
              "main.py"
          ],
          "env": {
              "SMTP_HOST": "",
              "SMTP_PORT": "",
              "SMTP_SECURE": "",
              "SMTP_USER": "",
              "SMTP_FROM": "",
              "SMTP_PASS": ""
          }
      }
  }
}
```

### Конфигурация Gmail

```json
"env": {
    "SMTP_HOST": "smtp.gmail.com",
    "SMTP_PORT": "587",
    "SMTP_SECURE": "false",
    "SMTP_USER": "your-email@gmail.com",
    "SMTP_FROM": "your-email@gmail.com",
    "SMTP_PASS": "your-app-password"
}
```

### Конфигурация Outlook

```json
"env": {
    "SMTP_HOST": "smtp-mail.outlook.com",
    "SMTP_PORT": "587",
    "SMTP_SECURE": "false",
    "SMTP_USER": "your-email@outlook.com",
    "SMTP_FROM": "your-email@outlook.com",
    "SMTP_PASS": "your-password"
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `send_email` | Быстрая отправка писем с использованием конфигурации из переменных окружения - укажите получателя, тему и текст с... |
| `send_custom_email` | Отправка писем с полным контролем, включая нескольких получателей с CC/BCC, файловые вложения, HTML ф... |
| `test_smtp_connection_tool` | Проверка настроек электронной почты и SMTP-соединения перед отправкой важных писем |

## Возможности

- Отправка как текстовых, так и HTML-писем
- Прикрепление файлов и документов
- Отправка нескольким людям с CC/BCC
- Проверка работоспособности настроек электронной почты
- Поддержка Gmail, Outlook и других почтовых провайдеров
- Переопределение SMTP настроек для отдельных писем
- Функциональность тестирования SMTP-соединения

## Переменные окружения

### Обязательные
- `SMTP_HOST` - Ваш почтовый сервер
- `SMTP_PORT` - Порт сервера
- `SMTP_SECURE` - Использовать SSL (true/false)
- `SMTP_USER` - Ваше имя пользователя
- `SMTP_FROM` - Адрес отправителя
- `SMTP_PASS` - Ваш пароль

## Примеры использования

```
Send an email to john@company.com saying the meeting is tomorrow at 2 PM
```

```
Send an HTML email to team@company.com with subject 'Weekly Update' and create a nice formatted message about this week's progress
```

```
Test the email connection to make sure it's working
```

```
Send a custom email to the team about the project update. Send to team@company.com, CC manager@company.com, and attach the project report
```

## Ресурсы

- [GitHub Repository](https://github.com/egyptianego17/email-mcp-server)

## Примечания

Для Gmail необходимо включить двухфакторную аутентификацию и использовать пароли приложений вместо обычных паролей. Сервер поддерживает множество почтовых провайдеров - большинство используют порт 587 с STARTTLS или порт 465 с SSL. Доступны команды для тестирования: 'uv run python test_email.py' для проверки конфигурации и 'uv run python test_email.py --send-real' для отправки реальных тестовых писем.