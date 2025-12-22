---
title: BrowserLoop MCP сервер
description: MCP сервер для создания скриншотов и чтения логов консоли с веб-страниц с использованием Playwright. Поддерживает высококачественную съемку с настраиваемыми форматами, размерами viewport, аутентификацией через cookie и скриншотами как полной страницы, так и отдельных элементов.
tags:
- Browser
- Web Scraping
- Monitoring
- DevOps
- API
author: mattiasw
featured: false
---

MCP сервер для создания скриншотов и чтения логов консоли с веб-страниц с использованием Playwright. Поддерживает высококачественную съемку с настраиваемыми форматами, размерами viewport, аутентификацией через cookie и скриншотами как полной страницы, так и отдельных элементов.

## Установка

### NPX (Рекомендуется)

```bash
# Установить браузер Chromium (одноразовая настройка)
npx playwright install chromium

# Проверить, что BrowserLoop работает
npx browserloop@latest --version
```

### Docker

```bash
# Скачать и запустить с Docker
docker run --rm --network host browserloop

# Или использовать docker-compose для разработки
git clone <repository-url>
cd browserloop
docker-compose -f docker/docker-compose.yml up
```

### Установка для разработки

```bash
# Клонировать репозиторий
git clone <repository-url>
cd browserloop

# Установить зависимости
npm install

# Установить браузеры Playwright (необходимо для скриншотов)
npx playwright install chromium

# Собрать проект
npm run build
```

## Конфигурация

### Конфигурация NPX

```json
{
  "mcpServers": {
    "browserloop": {
      "command": "npx",
      "args": ["-y", "browserloop@latest"],
      "description": "Screenshot and console log capture server for web pages using Playwright"
    }
  }
}
```

### Конфигурация для разработки

```json
{
  "mcpServers": {
    "browserloop": {
      "command": "node",
      "args": [
        "/absolute/path/to/browserloop/dist/src/index.js"
      ],
      "description": "Screenshot and console log capture server for web pages using Playwright"
    }
  }
}
```

### Конфигурация с переменными окружения

```json
{
  "mcpServers": {
    "browserloop": {
      "command": "node",
      "args": ["dist/src/mcp-server.js"],
      "env": {
        "BROWSERLOOP_DEFAULT_COOKIES": "/home/username/.config/browserloop/cookies.json",
        "BROWSERLOOP_DEFAULT_FORMAT": "webp",
        "BROWSERLOOP_DEFAULT_QUALITY": "85"
      }
    }
  }
}
```

## Возможности

- Высококачественная съемка скриншотов с использованием Playwright
- Мониторинг и сбор логов консоли с веб-страниц
- Поддержка localhost и удаленных URL
- Аутентификация через cookie для защищенных страниц
- Контейнеризация Docker для согласованных сред
- Поддержка форматов PNG, JPEG и WebP с настраиваемым качеством
- Безопасное выполнение в non-root контейнере
- Полная интеграция с MCP протоколом для инструментов разработки AI
- Настраиваемые размеры viewport и опции съемки
- Съемка полной страницы и отдельных элементов

## Переменные окружения

### Опциональные
- `BROWSERLOOP_DEFAULT_WIDTH` - Ширина viewport по умолчанию (200-4000)
- `BROWSERLOOP_DEFAULT_HEIGHT` - Высота viewport по умолчанию (200-4000)
- `BROWSERLOOP_DEFAULT_FORMAT` - Формат изображения по умолчанию (webp, png, jpeg)
- `BROWSERLOOP_DEFAULT_QUALITY` - Качество изображения по умолчанию (0-100)
- `BROWSERLOOP_DEFAULT_TIMEOUT` - Таймаут по умолчанию в миллисекундах
- `BROWSERLOOP_USER_AGENT` - Пользовательская строка user agent
- `BROWSERLOOP_DEFAULT_COOKIES` - Cookie по умолчанию как путь к файлу или JSON строка
- `BROWSERLOOP_CONSOLE_LOG_LEVELS` - Список уровней логирования через запятую для захвата

## Примеры использования

```
Take a screenshot of https://example.com
```

```
Take a screenshot of https://example.com with width 1920 and height 1080
```

```
Take a screenshot of https://example.com in JPEG format with 95% quality
```

```
Take a full page screenshot of https://example.com
```

```
Take a screenshot of http://localhost:3000 to verify the UI changes
```

## Ресурсы

- [GitHub Repository](https://github.com/mattiasw/browserloop)

## Примечания

⚠️ АРХИВИРОВАНО: Этот проект архивирован и больше не будет получать обновления. С выходом Chrome DevTools MCP выделенный MCP сервер для автоматизации браузера больше не нужен. Практически весь код в этом репозитории был автоматически сгенерирован. BrowserLoop требует установки Chromium через Playwright перед созданием скриншотов. Аутентификация через cookie поддерживается для захвата скриншотов защищенных паролем страниц во время разработки.