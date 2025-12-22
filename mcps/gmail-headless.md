---
title: Gmail Headless MCP сервер
description: Headless MCP сервер, который предоставляет функциональность Gmail (получение, отправка email) без необходимости локальной настройки учётных данных или доступа к файлам, разработан для удалённых/контейнеризированных сред.
tags:
- Messaging
- API
- Cloud
- Integration
- Productivity
author: baryhuang
featured: false
---

Headless MCP сервер, который предоставляет функциональность Gmail (получение, отправка email) без необходимости локальной настройки учётных данных или доступа к файлам, разработан для удалённых/контейнеризированных сред.

## Установка

### Из исходного кода

```bash
git clone https://github.com/baryhuang/mcp-headless-gmail.git
cd mcp-headless-gmail
pip install -e .
```

### Сборка Docker

```bash
docker build -t mcp-headless-gmail .
```

### Мультиплатформенный Docker

```bash
docker buildx create --use
docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 -t buryhuang/mcp-headless-gmail:latest --push .
```

## Конфигурация

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "gmail": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "buryhuang/mcp-headless-gmail:latest"
      ]
    }
  }
}
```

### Claude Desktop (NPM)

```json
{
  "mcpServers": {
    "gmail": {
      "command": "npx",
      "args": [
        "@peakmojo/mcp-server-headless-gmail"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `gmail_refresh_token` | Обновляет токены доступа, используя refresh token и клиентские учётные данные |
| `get_recent_emails` | Получает последние email с первыми 1000 символами содержимого каждого письма |
| `get_email_body` | Получает полное содержимое email частями по 1000 символов, используя параметр смещения для длинных писем |
| `send_email` | Отправляет email через Gmail с поддержкой как простого текста, так и HTML содержимого |

## Возможности

- Headless и удалённая работа - полностью работает в headless режиме в удалённых средах без браузера или доступа к локальным файлам
- Получение самых последних email из Gmail с первыми 1000 символами содержимого
- Получение полного содержимого email частями по 1000 символов с использованием параметра смещения
- Отправка email через Gmail с поддержкой HTML
- Отдельное обновление токенов доступа
- Автоматическая обработка refresh токенов
- Развязанная архитектура - клиенты самостоятельно проходят OAuth flow и передают учётные данные как контекст
- Готов для Docker с поддержкой контейнеризации
- Поддержка кроссплатформенных Docker образов (linux/amd64, linux/arm64, linux/arm/v7)

## Примеры использования

```
Получи мои последние непрочитанные письма
```

```
Отправь email кому-то с HTML форматированием
```

```
Получи полное содержимое длинного email сообщения
```

```
Обнови мой токен доступа к Gmail
```

## Ресурсы

- [GitHub Repository](https://github.com/baryhuang/mcp-headless-gmail)

## Примечания

Требует учётные данные Google API (client ID, client secret, access token, refresh token), передаваемые в вызовах инструментов, а не через переменные окружения. Поддерживает области Gmail: gmail.readonly и gmail.send. Построен на библиотеке google-api-python-client. Требует Python 3.10 или выше для локальной установки.