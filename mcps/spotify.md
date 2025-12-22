---
title: Spotify MCP сервер
description: MCP сервер, который подключает Claude к Spotify, обеспечивая управление воспроизведением, поиск музыки, управление очередью и операции с плейлистами через Spotify API.
tags:
- Media
- API
- Integration
- Productivity
author: Community
featured: false
---

MCP сервер, который подключает Claude к Spotify, обеспечивая управление воспроизведением, поиск музыки, управление очередью и операции с плейлистами через Spotify API.

## Установка

### UVX

```bash
uvx --python 3.12 --from git+https://github.com/varunneal/spotify-mcp spotify-mcp
```

### Локальное клонирование

```bash
git clone https://github.com/varunneal/spotify-mcp.git
chmod -R 755 /path/to/spotify-mcp
uv --directory /path/to/spotify-mcp run spotify-mcp
```

## Конфигурация

### Конфигурация UVX

```json
{
  "mcpServers": {
    "spotify": {
      "command": "uvx",
      "args": [
        "--python", "3.12",
        "--from", "git+https://github.com/varunneal/spotify-mcp",
        "spotify-mcp"
      ],
      "env": {
        "SPOTIFY_CLIENT_ID": "YOUR_CLIENT_ID",
        "SPOTIFY_CLIENT_SECRET": "YOUR_CLIENT_SECRET",
        "SPOTIFY_REDIRECT_URI": "http://127.0.0.1:8080/callback"
      }
    }
  }
}
```

### Локальная конфигурация

```json
{
  "spotify": {
    "command": "uv",
    "args": [
      "--directory",
      "/path/to/spotify-mcp",
      "run",
      "spotify-mcp"
    ],
    "env": {
      "SPOTIFY_CLIENT_ID": "YOUR_CLIENT_ID",
      "SPOTIFY_CLIENT_SECRET": "YOUR_CLIENT_SECRET",
      "SPOTIFY_REDIRECT_URI": "http://127.0.0.1:8080/callback"
    }
  }
}
```

## Возможности

- Запуск, пауза и пропуск воспроизведения
- Поиск треков/альбомов/исполнителей/плейлистов
- Получение информации о треке/альбоме/исполнителе/плейлисте
- Управление очередью Spotify
- Управление, создание и обновление плейлистов

## Переменные окружения

### Обязательные
- `SPOTIFY_CLIENT_ID` - ID клиентского приложения Spotify с developer.spotify.com
- `SPOTIFY_CLIENT_SECRET` - Секретный ключ клиентского приложения Spotify с developer.spotify.com
- `SPOTIFY_REDIRECT_URI` - URI перенаправления OAuth для аутентификации Spotify

## Ресурсы

- [GitHub Repository](https://github.com/varunneal/spotify-mcp)

## Примечания

Требуется аккаунт Spotify Premium для доступа к API разработчика. Создайте приложение на developer.spotify.com с URI перенаправления http://127.0.0.1:8080/callback. Может потребоваться перезапуск окружения MCP один или два раза перед началом работы. Построен поверх API от spotipy-dev. Логи отправляются в stderr и могут быть найдены в ~/Library/Logs/Claude на Mac. Используйте MCP Inspector для отладки: npx @modelcontextprotocol/inspector uv --directory /path/to/spotify-mcp run spotify-mcp