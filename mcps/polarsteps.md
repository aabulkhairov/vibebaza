---
title: Polarsteps MCP сервер
description: MCP сервер, который позволяет Claude и другим AI-ассистентам получать доступ к данным путешествий Polarsteps, давая пользователям возможность запрашивать профили, детали поездок, статистику путешествий и искать по истории поездок на естественном языке.
tags:
- API
- Analytics
- Search
- Integration
author: Community
featured: false
---

MCP сервер, который позволяет Claude и другим AI-ассистентам получать доступ к данным путешествий Polarsteps, давая пользователям возможность запрашивать профили, детали поездок, статистику путешествий и искать по истории поездок на естественном языке.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @remuzel/polarsteps-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/remuzel/polarsteps-mcp
cd polarsteps-mcp
just setup
# или без just:
uv sync --dev && uv pip install -e .
```

### Локальное тестирование

```bash
npx @modelcontextprotocol/inspector uvx --from git+https://github.com/remuzel/polarsteps-mcp polarsteps-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "polarsteps": {
      "command": "uvx",
      "args": ["--from", "git+https://github.com/remuzel/polarsteps-mcp", "polarsteps-mcp"],
      "env": {
        "POLARSTEPS_REMEMBER_TOKEN": "your_remember_token_here"
      }
    }
  }
}
```

## Возможности

- Профили пользователей: Получение информации о профиле, социальной статистики и метрик путешествий
- Данные поездок: Доступ к детальной информации о поездках, временным линиям и локациям
- Умный поиск: Поиск поездок по направлению, теме или ключевым словам с нечетким сопоставлением
- Аналитика путешествий: Получение комплексной статистики путешествий и достижений

## Переменные окружения

### Обязательные
- `POLARSTEPS_REMEMBER_TOKEN` - Токен аутентификации из cookies сайта Polarsteps для доступа к API

## Примеры использования

```
Покажи мне статистику путешествий для пользователя 'johndoe'
```

```
Расскажи о поездке johndoe в Японию
```

```
Какую страну johndoe стоит добавить в свой список желаний?
```

## Ресурсы

- [GitHub Repository](https://github.com/remuzel/polarsteps-mcp)

## Примечания

Этот MCP сервер использует пакет polarsteps-api для доступа к данным Polarsteps через недокументированные API. Пользователи должны прочитать соответствующий правовой отказ от ответственности и условия использования перед использованием этого инструмента. Чтобы получить remember_token: перейдите на polarsteps.com, будучи авторизованными, откройте инструменты разработчика браузера, найдите cookie remember_token и скопируйте его значение.