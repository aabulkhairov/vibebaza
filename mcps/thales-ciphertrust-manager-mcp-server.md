---
title: Thales CipherTrust Manager MCP сервер
description: Независимо разработанный MCP сервер, который позволяет AI-ассистентам вроде Claude взаимодействовать с ресурсами CipherTrust Manager для управления ключами, управления CTE клиентами, управления пользователями и криптографических операций с использованием CLI инструмента ksctl.
tags:
- Security
- API
- DevOps
- Integration
- Cloud
author: sanyambassi
featured: false
---

Независимо разработанный MCP сервер, который позволяет AI-ассистентам вроде Claude взаимодействовать с ресурсами CipherTrust Manager для управления ключами, управления CTE клиентами, управления пользователями и криптографических операций с использованием CLI инструмента ksctl.

## Установка

### Из исходников (вручную)

```bash
git clone https://github.com/sanyambassi/ciphertrust-manager-mcp-server.git
cd ciphertrust-manager-mcp-server
uv venv
.venv\Scripts\activate
uv pip install -e .
```

### Из исходников (winget)

```bash
winget install --id Python.Python.3.12 --source winget --accept-package-agreements --accept-source-agreements
pip install uv
git clone https://github.com/sanyambassi/ciphertrust-manager-mcp-server.git
cd ciphertrust-manager-mcp-server
uv venv
.venv\Scripts\activate
uv pip install -e .
```

### Прямой запуск

```bash
uv run ciphertrust-mcp-server
```

### Запуск как модуль

```bash
uv run python -m ciphertrust_mcp_server.__main__
```

## Конфигурация

### Claude Desktop (macOS/Linux)

```json
{
  "mcpServers": {
    "ciphertrust": {
      "command": "/absolute/path/to/ciphertrust-manager-mcp-server/.venv/bin/ciphertrust-mcp-server",
      "env": {
        "CIPHERTRUST_URL": "https://your-ciphertrust.example.com",
        "CIPHERTRUST_USER": "admin",
        "CIPHERTRUST_PASSWORD": "your-password-here"
      }
    }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "ciphertrust": {
      "command": "C:\\absolute\\path\\to\\ciphertrust-manager-mcp-server\\.venv\\Scripts\\ciphertrust-mcp-server",
      "env": {
        "CIPHERTRUST_URL": "https://your-ciphertrust.example.com",
        "CIPHERTRUST_USER": "admin",
        "CIPHERTRUST_PASSWORD": "your-password-here"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "ciphertrust": {
      "command": "Path to your project folder/ciphertrust-manager-mcp-server/.venv/bin/ciphertrust-mcp-server",
      "args": [],
      "env": {
        "CIPHERTRUST_URL": "https://your-ciphertrust.example.com",
        "CIPHERTRUST_USER": "admin",
        "CIPHERTRUST_PASSWORD": "your-password-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `key_management` | Операции управления ключами |
| `system_information` | Получение системной информации |

## Возможности

- Управление ключами
- Управление CTE клиентами
- Управление пользователями
- Управление подключениями
- Единый интерфейс для взаимодействия AI-ассистентов с CipherTrust Manager
- JSON-RPC коммуникация через stdin/stdout
- Настройка через переменные окружения
- Поддержка множественных доменов аутентификации

## Переменные окружения

### Обязательные
- `CIPHERTRUST_URL` - URL CipherTrust Manager (http/https)
- `CIPHERTRUST_USER` - имя пользователя CipherTrust Manager
- `CIPHERTRUST_PASSWORD` - пароль CipherTrust Manager

### Опциональные
- `CIPHERTRUST_NOSSLVERIFY` - отключить проверку SSL (true/false)
- `CIPHERTRUST_TIMEOUT` - таймаут для запросов к CipherTrust (в секундах)
- `CIPHERTRUST_DOMAIN` - домен CipherTrust по умолчанию
- `CIPHERTRUST_AUTH_DOMAIN` - домен аутентификации
- `KSCTL_PATH` - путь к бинарному файлу ksctl
- `KSCTL_CONFIG_PATH` - путь к конфигурационному файлу ksctl
- `LOG_LEVEL` - уровень логирования (DEBUG, INFO)

## Ресурсы

- [GitHub Repository](https://github.com/sanyambassi/ciphertrust-manager-mcp-server)

## Примечания

Это независимый проект с открытым исходным кодом, который официально не поддерживается компанией Thales. Использует публичные API и документированные интерфейсы. Требует доступ к экземпляру CipherTrust Manager. Включает в себя комплексные возможности тестирования с поддержкой MCP Inspector. Документация содержит подробные руководства по тестированию и примеры запросов.