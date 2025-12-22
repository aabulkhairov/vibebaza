---
title: Gopher MCP сервер
description: Современный кроссплатформенный MCP сервер, который позволяет AI-ассистентам безопасно и эффективно просматривать и взаимодействовать с ресурсами протоколов Gopher и Gemini.
tags:
- Web Scraping
- API
- Integration
- Security
- Productivity
author: Community
featured: false
---

Современный кроссплатформенный MCP сервер, который позволяет AI-ассистентам безопасно и эффективно просматривать и взаимодействовать с ресурсами протоколов Gopher и Gemini.

## Установка

### Установка для разработки

```bash
git clone https://github.com/cameronrye/gopher-mcp.git
cd gopher-mcp
./scripts/dev-setup.sh  # Unix/macOS
# или
scripts\dev-setup.bat   # Windows
uv run task serve
```

### Установка через PyPI

```bash
pip install gopher-mcp
# Или с uv
uv add gopher-mcp
```

### Установка с GitHub

```bash
uv add git+https://github.com/cameronrye/gopher-mcp.git
# Или установка в режиме разработки
git clone https://github.com/cameronrye/gopher-mcp.git
cd gopher-mcp
uv sync --all-extras
```

## Конфигурация

### Claude Desktop (Unix/macOS/Linux)

```json
{
  "mcpServers": {
    "gopher": {
      "command": "uv",
      "args": ["--directory", "/path/to/gopher-mcp", "run", "task", "serve"],
      "env": {
        "MAX_RESPONSE_SIZE": "1048576",
        "TIMEOUT_SECONDS": "30"
      }
    }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "gopher": {
      "command": "uv",
      "args": [
        "--directory",
        "C:\\path\\to\\gopher-mcp",
        "run",
        "task",
        "serve"
      ],
      "env": {
        "MAX_RESPONSE_SIZE": "1048576",
        "TIMEOUT_SECONDS": "30"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `gopher_fetch` | Получает Gopher-меню, текстовые файлы или метаданные по URL с комплексной обработкой ошибок и безопасностью... |
| `gemini_fetch` | Получает Gemini-контент с полной TLS-безопасностью, TOFU-валидацией сертификатов и нативным парсингом gemtext... |

## Возможности

- Поддержка двух протоколов: инструменты gopher_fetch и gemini_fetch для комплексного покрытия протоколов
- Полная поддержка Gopher: Обрабатывает меню (тип 1), текстовые файлы (тип 0), поисковые серверы (тип 7) и бинарные файлы
- Полная реализация Gemini: Нативный парсинг gemtext, TLS-безопасность и обработка кодов статуса
- Продвинутая безопасность: TOFU-валидация сертификатов, клиентские сертификаты и безопасные TLS-соединения
- Безопасность прежде всего: Встроенные тайм-ауты, ограничения размера, санитизация ввода и списки разрешенных хостов
- Оптимизировано для LLM: Возвращает структурированные JSON-ответы, предназначенные для потребления AI
- Кроссплатформенность: Работает без проблем на Windows, macOS и Linux
- Высокая производительность: Паттерны async/await с интеллектуальным кэшированием

## Переменные окружения

### Опциональные
- `GOPHER_MAX_RESPONSE_SIZE` - Максимальный размер ответа в байтах
- `GOPHER_TIMEOUT_SECONDS` - Тайм-аут запроса в секундах
- `GOPHER_CACHE_ENABLED` - Включить кэширование ответов
- `GOPHER_CACHE_TTL_SECONDS` - Время жизни кэша в секундах
- `GOPHER_ALLOWED_HOSTS` - Разрешенные хосты через запятую
- `GEMINI_MAX_RESPONSE_SIZE` - Максимальный размер ответа в байтах
- `GEMINI_TIMEOUT_SECONDS` - Тайм-аут запроса в секундах
- `GEMINI_CACHE_ENABLED` - Включить кэширование ответов

## Примеры использования

```
Просмотреть главное Gopher-меню на gopher.floodgap.com
```

```
Найти 'python' на поисковом сервере Veronica-2
```

```
Показать приветственный текст с Gopher-сервера Floodgap
```

```
Что доступно в каталоге Gopher-сообщества?
```

```
Получить домашнюю страницу протокола Gemini
```

## Ресурсы

- [GitHub Repository](https://github.com/cameronrye/gopher-mcp)

## Примечания

Требует Python 3.11+ и пакетный менеджер uv. Включает комплексную документацию, полное покрытие тестами и современные практики разработки с паттернами async/await.