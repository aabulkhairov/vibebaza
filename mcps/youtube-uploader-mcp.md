---
title: Youtube Uploader MCP сервер
description: Инструмент командной строки и MCP сервер для загрузки видео на YouTube с OAuth2 аутентификацией и управлением токенами.
tags:
- Media
- API
- Integration
- Productivity
author: anwerj
featured: false
---

Инструмент командной строки и MCP сервер для загрузки видео на YouTube с OAuth2 аутентификацией и управлением токенами.

## Установка

### Скачивание бинарного файла

```bash
Visit https://github.com/anwerj/youtube-uploader-mcp/releases and download the appropriate binary for your OS (youtube-uploader-mcp-linux-amd64, youtube-uploader-mcp-darwin-arm64, youtube-uploader-mcp-windows-amd64.exe)
```

### Сделать исполняемым

```bash
chmod +x path/to/youtube-uploader-mcp-<os>-<arch>
```

## Конфигурация

### Claude Desktop/Cursor

```json
{
  "mcpServers": {
    "youtube-uploader-mcp": {
      "command": "/absolute/path/to/youtube-uploader-mcp-<os>-<arch>",
      "args": [
        "-client_secret_file",
        "/absolute/path/to/client_secret.json(See Below)"
      ]
    }
  }
}
```

## Возможности

- Загрузка видео на YouTube через командную строку
- OAuth2 поток аутентификации
- Управление токенами доступа и обновления
- Модульная структура пакетов Go

## Ресурсы

- [GitHub Repository](https://github.com/anwerj/youtube-uploader-mcp)

## Примечания

Требует настройки Google OAuth 2.0 и файл client_secret.json из Google Developer Console. Пошаговое руководство доступно в youtube_oauth2_setup.md. Проект включает несколько пакетов Go: main/ для CLI входа, youtube/ для интеграции с API, tool/ для инструментов командной строки, и вспомогательные пакеты как hook/ и logn/.