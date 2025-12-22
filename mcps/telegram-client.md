---
title: Telegram-Client MCP сервер
description: Мост между Telegram API и AI-ассистентами, который позволяет управлять сообщениями, организовывать диалоги и общаться через Telegram в рамках AI-рабочих процессов.
tags:
- Messaging
- API
- Integration
- Productivity
- Communication
author: chaindead
featured: true
---

Мост между Telegram API и AI-ассистентами, который позволяет управлять сообщениями, организовывать диалоги и общаться через Telegram в рамках AI-рабочих процессов.

## Установка

### Homebrew

```bash
# Install
brew install chaindead/tap/telegram-mcp

# Update
brew upgrade chaindead/tap/telegram-mcp
```

### NPX

```bash
npx -y @chaindead/telegram-mcp
```

### Из релизов - MacOS Intel

```bash
# For Intel Mac (x86_64)
curl -L -o telegram-mcp.tar.gz https://github.com/chaindead/telegram-mcp/releases/latest/download/telegram-mcp_Darwin_x86_64.tar.gz

# Extract the binary
sudo tar xzf telegram-mcp.tar.gz -C /usr/local/bin

# Make it executable
sudo chmod +x /usr/local/bin/telegram-mcp

# Clean up
rm telegram-mcp.tar.gz
```

### Из релизов - MacOS Apple Silicon

```bash
# For Apple Silicon (M1/M2)
curl -L -o telegram-mcp.tar.gz https://github.com/chaindead/telegram-mcp/releases/latest/download/telegram-mcp_Darwin_arm64.tar.gz

# Extract the binary
sudo tar xzf telegram-mcp.tar.gz -C /usr/local/bin

# Make it executable
sudo chmod +x /usr/local/bin/telegram-mcp

# Clean up
rm telegram-mcp.tar.gz
```

### Из релизов - Linux x86_64

```bash
# For x86_64 (64-bit)
curl -L -o telegram-mcp.tar.gz https://github.com/chaindead/telegram-mcp/releases/latest/download/telegram-mcp_Linux_x86_64.tar.gz

# Extract the binary
sudo tar xzf telegram-mcp.tar.gz -C /usr/local/bin

# Make it executable
sudo chmod +x /usr/local/bin/telegram-mcp

# Clean up
rm telegram-mcp.tar.gz
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "telegram": {
      "command": "telegram-mcp",
      "env": {
        "TG_APP_ID": "<your-app-id>",
        "TG_API_HASH": "<your-api-hash>",
        "PATH": "<path_to_telegram-mcp_binary_dir>",
        "HOME": "<path_to_your_home_directory>"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "telegram-mcp": {
      "command": "telegram-mcp",
      "env": {
        "TG_APP_ID": "<your-app-id>",
        "TG_API_HASH": "<your-api-hash>"
      }
    }
  }
}
```

### Конфигурация NPX

```json
{
  "mcpServers": {
    "telegram": {
      "command": "npx",
      "args": ["-y", "@chaindead/telegram-mcp"],
      "env": {
        "TG_APP_ID": "<your-api-id>",
        "TG_API_HASH": "<your-api-hash>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `tg_me` | Получить информацию о текущем аккаунте |
| `tg_dialogs` | Список диалогов с опциональным фильтром непрочитанных |
| `tg_read` | Отметить диалог как прочитанный |
| `tg_dialog` | Получить сообщения из конкретного диалога |
| `tg_send` | Отправить черновики сообщений в любой диалог |

## Возможности

- Получение информации о текущем аккаунте
- Список диалогов с опциональным фильтром непрочитанных
- Отметка диалогов как прочитанных
- Получение сообщений из конкретного диалога
- Отправка черновиков сообщений в любой диалог

## Переменные окружения

### Обязательные
- `TG_APP_ID` - Ваш Telegram API ID
- `TG_API_HASH` - Ваш Telegram API hash

## Примеры использования

```
Проверь непрочитанные важные сообщения в моем Telegram
```

```
Суммируй все мои непрочитанные сообщения в Telegram
```

```
Прочитай и проанализируй мои непрочитанные сообщения, подготовь черновики ответов где нужно
```

```
Проверь некритичные непрочитанные сообщения и дай краткий обзор
```

```
Проанализируй мои диалоги в Telegram и предложи структуру папок
```

## Ресурсы

- [GitHub Repository](https://github.com/chaindead/telegram-mcp)

## Примечания

Требуются учетные данные Telegram API (API ID и hash) с https://my.telegram.org/auth. Необходима аутентификация через команду 'telegram-mcp auth' с вашим номером телефона и кодом подтверждения. Пользователи должны прочитать и понять Условия использования Telegram API перед использованием этого сервера. Поддерживает двухфакторную аутентификацию с флагом --password и переопределение сессии с флагом --new.