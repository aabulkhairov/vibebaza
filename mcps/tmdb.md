---
title: TMDB MCP сервер
description: Этот MCP сервер интегрируется с The Movie Database (TMDB) API для предоставления информации о фильмах, возможностей поиска и рекомендаций.
tags:
- API
- Media
- Search
- Database
author: Laksh-star
featured: false
---

Этот MCP сервер интегрируется с The Movie Database (TMDB) API для предоставления информации о фильмах, возможностей поиска и рекомендаций.

## Установка

### Из исходного кода

```bash
git clone [repository-url]
cd mcp-server-tmdb
npm install
npm run build
```

### Smithery

```bash
npx -y @smithery/cli install @Laksh-star/mcp-server-tmdb --client claude
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "tmdb": {
      "command": "/full/path/to/dist/index.js",
      "env": {
        "TMDB_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_movies` | Поиск фильмов по названию или ключевым словам, возвращает список фильмов с названиями, годами выпуска, ID, р... |
| `get_recommendations` | Получение рекомендаций фильмов на основе ID фильма, возвращает топ-5 рекомендуемых фильмов с подробностями |
| `get_trending` | Получение трендовых фильмов за определенный период времени (день или неделя), возвращает топ-10 трендовых фильмов с... |

## Возможности

- Поиск фильмов по названию или ключевым словам
- Получение рекомендаций фильмов на основе ID фильмов
- Получение трендовых фильмов (ежедневно или еженедельно)
- Доступ к подробной информации о фильмах, включая название, дату выхода, рейтинг, описание, жанры, URL постера, актерский состав, режиссера и отзывы
- Комплексная обработка ошибок для недействительных API ключей, сетевых ошибок, недействительных ID фильмов и некорректных запросов

## Переменные окружения

### Обязательные
- `TMDB_API_KEY` - API ключ из TMDB панели управления для доступа к The Movie Database API

## Примеры использования

```
Search for movies about artificial intelligence
```

```
What are the trending movies today?
```

```
Show me this week's trending movies
```

```
Get movie recommendations based on movie ID 550
```

```
Tell me about the movie with ID 550
```

## Ресурсы

- [GitHub Repository](https://github.com/Laksh-star/mcp-server-tmdb)

## Примечания

Требует учетную запись TMDB и одобрение API ключа. Поддерживает macOS и Linux. Ресурсы фильмов доступны через формат URI tmdb:///movie/<movie_id>. Режим разработки с отслеживанием изменений доступен с помощью 'npm run watch'.