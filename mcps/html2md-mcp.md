---
title: html2md-mcp MCP сервер
description: MCP сервер для конвертации HTML веб-страниц в чистый Markdown формат с уменьшением размера на 90-95%, включающий автоматизацию браузера с Playwright для сайтов с большим количеством JavaScript и страниц с аутентификацией.
tags:
- Web Scraping
- Browser
- Productivity
- AI
- Integration
author: Community
featured: false
---

MCP сервер для конвертации HTML веб-страниц в чистый Markdown формат с уменьшением размера на 90-95%, включающий автоматизацию браузера с Playwright для сайтов с большим количеством JavaScript и страниц с аутентификацией.

## Установка

### uv (рекомендуется)

```bash
# Clone the repository
git clone <your-repo-url>
cd html2md

# Install dependencies
uv pip install -e .

# Install Playwright browsers (required for browser mode)
playwright install chromium
```

### pip

```bash
# Clone the repository
git clone <your-repo-url>
cd html2md

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -e .

# Install Playwright browsers (required for browser mode)
playwright install chromium
```

### Docker

```bash
# Build the image
docker build -t html2md .

# Or use pre-built image (when published)
docker pull your-registry/html2md:latest
```

## Конфигурация

### Claude Desktop (macOS)

```json
{
  "mcpServers": {
    "html2md": {
      "command": "uv",
      "args": [
        "--directory",
        "/absolute/path/to/html2md",
        "run",
        "html2md"
      ]
    }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "html2md": {
      "command": "uv",
      "args": [
        "--directory",
        "C:\\absolute\\path\\to\\html2md",
        "run",
        "html2md"
      ]
    }
  }
}
```

### Claude Desktop (Linux)

```json
{
  "mcpServers": {
    "html2md": {
      "command": "uv",
      "args": [
        "--directory",
        "/absolute/path/to/html2md",
        "run",
        "html2md"
      ]
    }
  }
}
```

### Docker

```json
{
  "mcpServers": {
    "html2md": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "html2md"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `html_to_markdown` | Конвертирует HTML веб-страницы в чистый Markdown формат с настраиваемыми опциями для изображений, таблиц, ссылок... |

## Возможности

- Конвертация HTML из URL в чистый Markdown
- Сохранение таблиц, изображений и ссылок
- Удаление ненужных элементов (скрипты, стили, навигация, футеры, заголовки)
- Значительное уменьшение размера (обычно сжатие на 90-95%)
- Настраиваемые опции для изображений, таблиц и ссылок
- Создан с использованием trafilatura и BeautifulSoup4 для надежного извлечения
- Потоковая обработка для эффективной работы с большими страницами
- Ограничения размера для предотвращения загрузки слишком большого контента (1MB-50MB)
- Опциональное кэширование для ускорения повторных конвертаций тех же URL
- Режим браузера с Playwright - обрабатывает сайты с большим количеством JavaScript и аутентифицированные страницы

## Примеры использования

```
Convert this webpage to markdown: https://example.com/article
```

```
Use the html_to_markdown tool with url: https://example.com/docs, include_images: false, include_tables: true
```

```
Use the html_to_markdown tool with url: https://spa-application.com, fetch_method: playwright, wait_for: networkidle
```

```
Use the html_to_markdown tool with url: https://private-site.com/dashboard, fetch_method: playwright, use_user_profile: true, browser_type: chromium
```

## Ресурсы

- [GitHub Repository](https://github.com/sunshad0w/html2md-mcp)

## Примечания

Требует Python 3.10 или выше. Для функциональности режима браузера должны быть установлены браузеры Playwright. Docker образ включает предустановленный Playwright с Chromium и оптимизирован для продакшн использования. При использовании режима пользовательского профиля Chrome должен быть закрыт. Обычная производительность показывает сжатие на 90-95% от оригинального размера HTML.