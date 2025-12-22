---
title: mcp-notify MCP сервер
description: MCP сервер, который предоставляет возможности отправки сообщений, поддерживая уведомления через WeChat Work, DingTalk, Telegram, Bark, Lark, Feishu и Home Assistant.
tags:
- Messaging
- Integration
- API
- Productivity
- Monitoring
author: aahl
featured: false
install_command: claude mcp add notify -- uvx mcp-notify
---

MCP сервер, который предоставляет возможности отправки сообщений, поддерживая уведомления через WeChat Work, DingTalk, Telegram, Bark, Lark, Feishu и Home Assistant.

## Установка

### uvx

```bash
uvx mcp-notify
```

### Smithery

```bash
Use OAuth authorization or Smithery key at https://smithery.ai/server/@aahl/mcp-notify
```

### Docker

```bash
mkdir /opt/mcp-notify
cd /opt/mcp-notify
wget https://raw.githubusercontent.com/aahl/mcp-notify/refs/heads/main/docker-compose.yml
docker-compose up -d
```

## Конфигурация

### Конфигурация uvx

```json
{
  "mcpServers": {
    "mcp-notify": {
      "command": "uvx",
      "args": ["mcp-notify"],
      "env": {
        "WEWORK_BOT_KEY": "your-wework-bot-key"
      }
    }
  }
}
```

### Конфигурация Smithery

```json
{
  "mcpServers": {
    "mcp-aktools": {
      "url": "https://server.smithery.ai/@aahl/mcp-notify/mcp"
    }
  }
}
```

### Конфигурация Docker

```json
{
  "mcpServers": {
    "mcp-notify": {
      "url": "http://0.0.0.0:8809/mcp"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `wework_send_text` | Отправка текстовых или Markdown сообщений через групповой бот WeChat Work |
| `wework_send_image` | Отправка изображений через групповой бот WeChat Work |
| `wework_send_news` | Отправка новостных сообщений через групповой бот WeChat Work |
| `wework_app_send_text` | Отправка текстовых или Markdown сообщений через приложение WeChat Work |
| `wework_app_send_image` | Отправка изображений через приложение WeChat Work |
| `wework_app_send_video` | Отправка видео через приложение WeChat Work |
| `wework_app_send_voice` | Отправка голосовых сообщений через приложение WeChat Work |
| `wework_app_send_file` | Отправка файлов через приложение WeChat Work |
| `wework_app_send_news` | Отправка новостных сообщений через приложение WeChat Work |
| `tg_send_message` | Отправка текстовых или Markdown сообщений через Telegram Bot |
| `tg_send_photo` | Отправка фотографий через Telegram Bot |
| `tg_send_video` | Отправка видео через Telegram Bot |
| `tg_send_audio` | Отправка аудио через Telegram Bot |
| `tg_send_file` | Отправка файлов через Telegram Bot |
| `tg_markdown_rule` | Получение правил форматирования Markdown для Telegram |

## Возможности

- Поддержка нескольких платформ обмена сообщениями (WeChat Work, DingTalk, Telegram и др.)
- Отправка текстовых, изображений, видео, аудио и файловых сообщений
- Обмен сообщениями через групповые боты и приложения
- Поддержка форматирования Markdown
- Преобразование текста в речь
- Интеграция с Home Assistant
- Несколько вариантов деплоя (uvx, Docker, Smithery)

## Переменные окружения

### Опциональные
- `WEWORK_BOT_KEY` - Ключ по умолчанию для группового бота WeChat Work
- `WEWORK_APP_CORPID` - ID предприятия WeChat Work
- `WEWORK_APP_SECRET` - Секрет приложения WeChat Work
- `WEWORK_APP_AGENTID` - ID приложения WeChat Work (по умолчанию: 1000002)
- `WEWORK_APP_TOUSER` - ID получателя по умолчанию WeChat Work (по умолчанию: @all)
- `WEWORK_BASE_URL` - Адрес прокси API WeChat Work (по умолчанию: https://qyapi.weixin.qq.com)
- `DINGTALK_BOT_KEY` - access_token для группового бота DingTalk
- `DINGTALK_BASE_URL` - Адрес API DingTalk (по умолчанию: https://oapi.dingtalk.com)

## Ресурсы

- [GitHub Repository](https://github.com/aahl/mcp-notify)

## Примечания

Сервер поддерживает документацию как на китайском, так и на английском языках. Доступны несколько вариантов быстрого старта, включая онлайн-тестирование на FastMCP.cloud и Smithery.ai, а также прямую интеграцию с различными IDE и редакторами.