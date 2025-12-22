---
title: scrapling-fetch MCP сервер
description: MCP сервер, который помогает AI ассистентам получать доступ к текстовому контенту с веб-сайтов, использующих защиту от ботов, заполняя пробел между тем, что вы видите в браузере, и тем, к чему может получить доступ AI.
tags:
- Web Scraping
- Browser
- Security
- API
- Integration
author: cyberchitta
featured: false
---

MCP сервер, который помогает AI ассистентам получать доступ к текстовому контенту с веб-сайтов, использующих защиту от ботов, заполняя пробел между тем, что вы видите в браузере, и тем, к чему может получить доступ AI.

## Установка

### Установка через UV Tool

```bash
# Install scrapling-fetch-mcp
uv tool install scrapling-fetch-mcp

# Install browser binaries (REQUIRED - large downloads)
uvx --from scrapling-fetch-mcp scrapling install
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "scrapling-fetch": {
      "command": "uvx",
      "args": ["scrapling-fetch-mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `page_fetching` | Получает полные веб-страницы с поддержкой пагинации |
| `pattern_extraction` | Находит и извлекает определенный контент используя regex паттерны |

## Возможности

- Обход защиты от ботов с тремя режимами защиты (basic, stealth, max-stealth)
- Автоматическая поддержка пагинации для больших страниц
- Извлечение текстового/HTML контента с защищенных веб-сайтов
- Поиск по паттернам для специфичного контента
- Автоматическое переключение с базового на стелс режимы по мере необходимости
- Оптимизирован для получения документации и справочных материалов в небольших объемах

## Примеры использования

```
Can you fetch the docs at https://example.com/api
```

```
Find all mentions of 'authentication' on that page
```

```
Get me the installation instructions from their homepage
```

## Ресурсы

- [GitHub Repository](https://github.com/cyberchitta/scrapling-fetch-mcp)

## Примечания

Требует Python 3.10+ и пакетный менеджер uv. Установка браузера скачивает сотни МБ и должна завершиться перед первым использованием. Разработан только для текстового контента, не для скрапинга больших объемов. Может не работать с сайтами, требующими аутентификации. Создан с использованием Scrapling для веб-скрапинга с обходом защиты от ботов.