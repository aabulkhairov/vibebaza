---
title: Arr Suite MCP сервер
description: Комплексный MCP сервер, который предоставляет AI-ассистентам интеллектуальный доступ ко всему вашему стеку автоматизации медиа arr suite, включая Sonarr, Radarr, Prowlarr, Bazarr, Overseerr и Plex с обработкой естественного языка.
tags:
- Media
- Integration
- AI
- API
- Monitoring
author: shaktech786
featured: false
---

Комплексный MCP сервер, который предоставляет AI-ассистентам интеллектуальный доступ ко всему вашему стеку автоматизации медиа arr suite, включая Sonarr, Radarr, Prowlarr, Bazarr, Overseerr и Plex с обработкой естественного языка.

## Установка

### Из PyPI

```bash
pip install arr-suite-mcp
```

### Из исходников

```bash
git clone https://github.com/shaktech786/arr-suite-mcp-server.git
cd arr-suite-mcp-server
pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "arr-suite": {
      "command": "arr-suite-mcp",
      "env": {
        "SONARR_HOST": "localhost",
        "SONARR_PORT": "8989",
        "SONARR_API_KEY": "your_api_key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `arr_execute` | Выполняет любую arr операцию используя естественный язык |
| `arr_explain_intent` | Понимает как ваш запрос будет интерпретирован |
| `arr_list_services` | Показывает настроенные сервисы |
| `arr_get_system_status` | Получает статус здоровья всех сервисов |
| `sonarr_search_series` | Поиск TV сериалов |
| `sonarr_add_series` | Добавляет новый сериал |
| `sonarr_get_series` | Получает все или конкретные сериалы |
| `radarr_search_movie` | Поиск фильмов |
| `radarr_add_movie` | Добавляет новый фильм |
| `radarr_get_movies` | Получает все или конкретные фильмы |
| `prowlarr_search` | Поиск по индексаторам |
| `prowlarr_get_indexers` | Список всех индексаторов |
| `prowlarr_sync_apps` | Синхронизация с приложениями |
| `plex_search` | Поиск медиа в Plex |
| `plex_get_libraries` | Список всех библиотек |

## Возможности

- Интеллектуальное распознавание намерений используя понимание естественного языка
- Унифицированный интерфейс для всех arr сервисов
- Поддержка Sonarr, Radarr, Prowlarr, Bazarr, Overseerr и Plex
- Типобезопасность построен с Pydantic для надежной валидации
- Async-первый построен на httpx для высокопроизводительных операций
- Комплексное покрытие API для всех поддерживаемых сервисов
- Обработка естественного языка для человекоподобных взаимодействий
- Утилиты управления базой данных для бэкапа и восстановления
- Управление очередями и мониторинг всех сервисов
- Управление профилями качества и корневыми папками

## Переменные окружения

### Опциональные
- `SONARR_HOST` - Имя хоста сервера Sonarr
- `SONARR_PORT` - Порт сервера Sonarr
- `SONARR_API_KEY` - API ключ Sonarr
- `RADARR_HOST` - Имя хоста сервера Radarr
- `RADARR_PORT` - Порт сервера Radarr
- `RADARR_API_KEY` - API ключ Radarr
- `PROWLARR_HOST` - Имя хоста сервера Prowlarr
- `PROWLARR_PORT` - Порт сервера Prowlarr

## Примеры использования

```
Добавить Во все тяжкие в мою коллекцию
```

```
Найти Мандалорца
```

```
Список всех моих TV шоу
```

```
Добавить Матрицу в мои фильмы
```

```
Найти Начало
```

## Ресурсы

- [GitHub Repository](https://github.com/shaktech786/arr-suite-mcp-server)

## Примечания

Требует API ключи для каждого сервиса, который вы хотите интегрировать. Поддерживает как высокоуровневые команды на естественном языке, так и специфичные для сервиса инструменты. Включает утилиты управления базой данных и комплексное покрытие API для всех поддерживаемых сервисов arr suite.