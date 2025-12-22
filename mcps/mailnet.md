---
title: MailNet MCP сервер
description: Унифицированный MCP сервер для оркестрации email, поддерживающий Gmail и Outlook со стандартизированными метаданными, безопасной инжекцией учетных данных и агентными email-воркфлоу для управления почтой через ассистентов.
tags:
- Messaging
- Integration
- AI
- Productivity
- API
author: Community
featured: false
---

Унифицированный MCP сервер для оркестрации email, поддерживающий Gmail и Outlook со стандартизированными метаданными, безопасной инжекцией учетных данных и агентными email-воркфлоу для управления почтой через ассистентов.

## Установка

### Из исходного кода

```bash
git clone https://github.com/Astroa7m/MailNet-MCP-Server.git
cd MailNet-MCP-Server
pip install -r requirements.txt
```

### UV Run

```bash
uv run -m mcp_launcher.server
```

### Python Run

```bash
python -m mcp_launcher.server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpservers": {
    "email_mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "C:\\Path\\To\\mcp-server",
        "run",
        "-m",
        "mcp_launcher.server"
      ],
      "env": {
        "AZURE_APPLICATION_CLIENT_ID": "<AZURE_APPLICATION_CLIENT_ID>",
        "AZURE_CLIENT_SECRET_VALUE": "<AZURE_CLIENT_SECRET_VALUE>",
        "AZURE_PREFERRED_TOKEN_FILE_PATH": "C:\\Path\\To\\azure_token.json",
        "GOOGLE_CREDENTIALS_FILE_PATH": "C:\\Path\\To\\google_credentials.json",
        "GOOGLE_PREFERRED_TOKEN_FILE_PATH": "C:\\Path\\To\\google_token.json"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `send_email` | Создание и отправка сообщений |
| `read_email` | Получение и просмотр сообщений |
| `create_draft` | Подготовка сообщений |
| `send_draft` | Финализация и отправка |
| `search_email` | Поиск в почтовом ящике с семантическими фильтрами |
| `toggle_label` | Изменение категорий/меток |
| `archive_email` | Очистка почтового ящика |
| `reply_email` | Ответ в контексте переписки |
| `delete_email` | Удаление сообщений |
| `load_email_settings` | Просмотр текущих настроек почты |
| `update_email_settings` | Обновление настроек почты в рантайме |

## Возможности

- Унифицированная абстракция Gmail + Outlook
- Автоматическое обновление токенов и управление учетными данными
- Стандартизированный базовый класс для расширения провайдеров
- Агентный endpoint настроек email (тон, подпись, контекст переписки и т.д.)
- Модульный набор инструментов: отправка, чтение, поиск, метки, архив, ответы, удаление, черновики

## Переменные окружения

### Обязательные
- `GOOGLE_CREDENTIALS_FILE_PATH` - Путь к JSON файлу с учетными данными Google
- `GOOGLE_PREFERRED_TOKEN_FILE_PATH` - Путь к JSON файлу с токеном Google
- `AZURE_APPLICATION_CLIENT_ID` - ID клиентского приложения Azure для Outlook
- `AZURE_CLIENT_SECRET_VALUE` - Секрет клиента Azure для Outlook
- `AZURE_PREFERRED_TOKEN_FILE_PATH` - Путь к JSON файлу с токеном Azure

## Ресурсы

- [GitHub Repository](https://github.com/Astroa7m/MailNet-MCP-Server)

## Примечания

Требует установки UV для Windows: powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex". Смотрите Azure Authorization Guide и Google Authorization Guide для настройки аккаунтов и токенов. Сервер модульный и расширяемый - наследуйте базовый клиент для добавления новых провайдеров.