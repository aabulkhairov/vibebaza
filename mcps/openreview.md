---
title: OpenReview MCP сервер
description: MCP сервер, который предоставляет доступ к данным OpenReview для исследований и анализа, позволяя искать пользователей, получать статьи и экспортировать исследовательские данные с крупных ML конференций (ICML, ICLR, NeurIPS).
tags:
- AI
- Search
- Analytics
- API
- Database
author: anyakors
featured: false
install_command: claude mcp add-json openreview '{"command":"openreview-mcp-server","cwd":"/install/dir/openreview-mcp-server","env":{"OPENREVIEW_USERNAME":"username","OPENREVIEW_PASSWORD":"password","OPENREVIEW_BASE_URL":"https://api2.openreview.net","OPENREVIEW_DEFAULT_EXPORT_DIR":"./openreview_exports"}}'
---

MCP сервер, который предоставляет доступ к данным OpenReview для исследований и анализа, позволяя искать пользователей, получать статьи и экспортировать исследовательские данные с крупных ML конференций (ICML, ICLR, NeurIPS).

## Установка

### Из исходного кода

```bash
pip install -e .
```

## Конфигурация

### Claude Code

```json
{
  "mcpServers": {
    "openreview": {
      "command": "python",
      "args": ["-m", "openreview_mcp_server"],
      "env": {
        "OPENREVIEW_USERNAME": "your_email@domain.com",
        "OPENREVIEW_PASSWORD": "your_password"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_user` | Найти профиль пользователя по email адресу |
| `get_user_papers` | Получить все статьи, опубликованные конкретным пользователем |
| `get_conference_papers` | Получить статьи с конкретной конференции и года |
| `search_papers` | Искать статьи по ключевым словам среди нескольких конференций |
| `export_papers` | Экспортировать результаты поиска в JSON файлы для анализа |

## Возможности

- Поиск пользователей: найти профили OpenReview по email адресу
- Получение статей: получить все статьи конкретного автора
- Статьи конференций: получить статьи с определенных площадок (ICLR, NeurIPS, ICML) и годов
- Поиск по ключевым словам: искать статьи по ключевым словам среди нескольких конференций
- JSON&PDF экспорт: экспортировать результаты поиска в PDF и JSON файлы для удобного чтения или дальнейшего анализа и использования с ассистентами

## Переменные окружения

### Обязательные
- `OPENREVIEW_USERNAME` - Ваш email адрес OpenReview
- `OPENREVIEW_PASSWORD` - Ваш пароль OpenReview

### Опциональные
- `OPENREVIEW_BASE_URL` - Базовый URL API OpenReview
- `OPENREVIEW_DEFAULT_EXPORT_DIR` - Директория по умолчанию для экспорта

## Примеры использования

```
Can you please search papers using openreview mcp with keywords "time series token merging", match all keywords, venues ICLR and ICML 2025?
```

```
Please export the contents of this paper.
```

```
Search for papers on time series forecasting in ICLR 2024
```

```
Export relevant papers about neural networks to JSON files
```

## Ресурсы

- [GitHub Repository](https://github.com/anyakors/openreview-mcp-server)

## Примечания

Поддерживает конференции ICLR, NeurIPS и ICML. Предоставляет несколько режимов поиска (любое, все, точное) и может экспортировать статьи с возможностью скачивания PDF и извлечения текста.