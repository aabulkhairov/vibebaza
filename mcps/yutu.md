---
title: yutu MCP сервер
description: Полнофункциональный MCP сервер и CLI для YouTube для автоматизации работы с YouTube. Может управлять практически всеми ресурсами YouTube, такими как видео, плейлисты, каналы, комментарии, субтитры и многое другое.
tags:
- Media
- API
- Productivity
- Integration
- Analytics
author: eat-pray-ai
featured: true
---

Полнофункциональный MCP сервер и CLI для YouTube для автоматизации работы с YouTube. Может управлять практически всеми ресурсами YouTube, такими как видео, плейлисты, каналы, комментарии, субтитры и многое другое.

## Установка

### Docker

```bash
docker pull ghcr.io/eat-pray-ai/yutu:latest
docker run --rm ghcr.io/eat-pray-ai/yutu:latest
```

### Go Install

```bash
go install github.com/eat-pray-ai/yutu@latest
```

### Linux Shell Script

```bash
curl -sSfL https://raw.githubusercontent.com/eat-pray-ai/yutu/main/scripts/install.sh | bash
```

### Homebrew (macOS)

```bash
brew install yutu
```

### WinGet (Windows)

```bash
winget install yutu
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "yutu": {
    "type": "stdio",
    "command": "yutu",
    "args": [
      "mcp"
    ],
    "env": {
      "YUTU_CREDENTIAL": "/absolute/path/to/client_secret.json",
      "YUTU_CACHE_TOKEN": "/absolute/path/to/youtube.token.json"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `activity` | Список активностей YouTube |
| `auth` | Аутентификация с YouTube API |
| `caption` | Управление субтитрами YouTube |
| `channel` | Управление каналами YouTube |
| `channelBanner` | Вставка баннера канала YouTube |
| `channelSection` | Управление разделами каналов YouTube |
| `comment` | Управление комментариями YouTube |
| `commentThread` | Управление цепочками комментариев YouTube |
| `playlist` | Управление плейлистами YouTube |
| `playlistImage` | Управление изображениями плейлистов YouTube |
| `playlistItem` | Управление элементами плейлистов YouTube |
| `search` | Поиск ресурсов YouTube |
| `subscription` | Управление подписками YouTube |
| `thumbnail` | Установка миниатюры для видео |
| `video` | Управление видео YouTube |

## Возможности

- Управление видео, плейлистами, каналами, комментариями, субтитрами
- Аутентификация YouTube и управление токенами
- Поиск ресурсов YouTube
- Управление баннерами каналов и водяными знаками
- Обработка подписок и членств
- Поддержка YouTube Analytics и Reporting API
- Доступен как CLI, так и MCP сервер

## Переменные окружения

### Обязательные
- `YUTU_CREDENTIAL` - Путь к JSON файлу с OAuth клиентскими данными Google Cloud
- `YUTU_CACHE_TOKEN` - Путь к JSON файлу с токеном YouTube для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/eat-pray-ai/yutu)

## Примечания

Требует проект Google Cloud Platform с включенным YouTube Data API v3 и OAuth учетными данными. Необходимо пройти аутентификацию с YouTube API используя команду 'yutu auth' перед использованием функциональности MCP сервера. Поддерживает YouTube Analytics API и YouTube Reporting API как опциональные возможности.