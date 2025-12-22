---
title: Restream MCP сервер
description: Сервер Model Context Protocol, который предоставляет инструменты для взаимодействия с Restream API для управления потоковыми каналами, контроля стримов и доступа к аналитике через естественный язык.
tags:
- Media
- Analytics
- API
- Integration
- Monitoring
author: shaktech786
featured: false
---

Сервер Model Context Protocol, который предоставляет инструменты для взаимодействия с Restream API для управления потоковыми каналами, контроля стримов и доступа к аналитике через естественный язык.

## Установка

### NPM Global

```bash
npm install -g @shaktech786/restream-mcp-server
```

### NPM Local

```bash
npm install @shaktech786/restream-mcp-server
```

### Из исходников

```bash
git clone https://github.com/shaktech786/restream-mcp-server.git
cd restream-mcp-server
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPM)

```json
{
  "mcpServers": {
    "restream": {
      "command": "npx",
      "args": ["-y", "@shaktech786/restream-mcp-server"],
      "env": {
        "RESTREAM_CLIENT_ID": "your_client_id_here",
        "RESTREAM_CLIENT_SECRET": "your_client_secret_here",
        "RESTREAM_API_BASE_URL": "https://api.restream.io/v2"
      }
    }
  }
}
```

### Claude Desktop (исходники)

```json
{
  "mcpServers": {
    "restream": {
      "command": "node",
      "args": ["/absolute/path/to/restream-mcp-server/dist/index.js"],
      "env": {
        "RESTREAM_CLIENT_ID": "your_client_id_here",
        "RESTREAM_CLIENT_SECRET": "your_client_secret_here",
        "RESTREAM_API_BASE_URL": "https://api.restream.io/v2"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_user_profile` | Получить информацию профиля аутентифицированного пользователя, включая email, отображаемое имя и данные аккаунта |
| `list_channels` | Список всех подключенных потоковых каналов/платформ (YouTube, Twitch, Facebook и др.) с их подключением... |
| `get_channel` | Получить подробную информацию о конкретном канале по ID |
| `update_channel_status` | Включить или отключить конкретный потоковый канал |
| `get_current_stream` | Получить информацию о текущем/активном стриме, включая название, статус, RTMP URL и количество зрителей |
| `update_stream_settings` | Обновить настройки текущего стрима, такие как название, описание или настройки приватности |
| `get_stream_analytics` | Получить аналитику и статистику для стримов, включая количество зрителей, метрики вовлеченности и производительности... |
| `start_stream` | Начать новый стрим с дополнительными настройками |
| `stop_stream` | Остановить текущий активный стрим |

## Возможности

- Управление профилем пользователя: получение информации об аутентифицированном пользователе
- Управление каналами: просмотр списка, просмотр, включение/отключение потоковых каналов
- Контроль стримов: запуск, остановка и обновление настроек стрима
- Аналитика: доступ к аналитике стриминга и данным о производительности
- OAuth аутентификация: безопасный доступ к API с использованием учетных данных клиента

## Переменные окружения

### Обязательные
- `RESTREAM_CLIENT_ID` - Ваш client ID для Restream API
- `RESTREAM_CLIENT_SECRET` - Ваш client secret для Restream API

### Опциональные
- `RESTREAM_API_BASE_URL` - Базовый URL для Restream API

## Примеры использования

```
Покажи все мои подключенные потоковые каналы
```

```
Получи информацию о моем текущем стриме
```

```
Обнови название моего стрима на 'Сессия программирования в прямом эфире'
```

```
Включи мой YouTube канал
```

```
Покажи мою аналитику стриминга
```

## Ресурсы

- [GitHub Repository](https://github.com/shaktech786/restream-mcp-server)

## Примечания

Требует Node.js 18 или выше и учетные данные Restream API из Restream Developer Portal. Сервер поддерживает OAuth аутентификацию и предоставляет комплексное управление стримами на множестве платформ, таких как YouTube, Twitch и Facebook.