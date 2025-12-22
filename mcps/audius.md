---
title: Audius MCP сервер
description: MCP сервер, предоставляющий комплексный доступ к музыкальной платформе Audius через LLM, с 105 инструментами, покрывающими ~95% Audius Protocol API для поиска музыки, стриминга, создания контента и социальных взаимодействий.
tags:
- Media
- API
- Analytics
- Finance
- Integration
author: glassBead-tc
featured: false
install_command: claude mcp add audius npx audius-mcp-atris
---

MCP сервер, предоставляющий комплексный доступ к музыкальной платформе Audius через LLM, с 105 инструментами, покрывающими ~95% Audius Protocol API для поиска музыки, стриминга, создания контента и социальных взаимодействий.

## Установка

### NPM

```bash
npm install audius-mcp-atris
```

### Yarn

```bash
yarn add audius-mcp-atris
```

### NPX

```bash
npx audius-mcp-atris
```

### Global NPM

```bash
npm install -g audius-mcp-atris
```

### Из исходного кода

```bash
git clone https://github.com/glassBead/audius-mcp-atris.git
cd audius-mcp-atris
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "audius": {
      "command": "npx",
      "args": [
        "audius-mcp-atris"
      ],
      "env": {
        "AUDIUS_API_KEY": "your_api_key_here",
        "AUDIUS_API_SECRET": "your_api_secret_here"
      }
    }
  }
}
```

### Claude Desktop (локально)

```json
{
  "mcpServers": {
    "audius": {
      "command": "audius-mcp-atris",
      "env": {
        "AUDIUS_API_KEY": "your_api_key_here",
        "AUDIUS_API_SECRET": "your_api_secret_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search-tracks` | Поиск треков с различными фильтрами |
| `get-trending-tracks` | Открывайте популярное на Audius |
| `similar-artists` | Находите исполнителей, похожих на тех, которые вам нравятся |
| `upload-track` | Добавляйте новые треки на Audius |
| `create-playlist` | Создавайте коллекции треков |
| `follow-user` | Подписывайтесь на других пользователей |
| `favorite-track` | Сохраняйте и выражайте признательность музыке |
| `add-track-comment` | Добавляйте комментарии к трекам |
| `purchase-track` | Покупайте премиум-контент с различными способами оплаты |
| `track-access-gates` | Проверяйте и подтверждайте доступ на основе NFT |

## Возможности

- Доступ к трекам, пользователям, плейлистам, альбомам и поиск на Audius
- Скачивание треков, изучение технических деталей, доступ к стемам
- Поиск покупателей треков, ремиксеров и связанных исполнителей
- Персонализированные рекомендации, история пользователя, тренды по жанрам
- Стрим треков напрямую в ваш клиент или открытие их в Audius Desktop
- Загрузка треков, создание плейлистов, управление вашим контентом на Audius
- Подписка на пользователей, добавление треков в избранное, комментирование контента
- Доступ к премиум-контенту, покупка треков, отправка чаевых исполнителям
- Отслеживание количества воспроизведений, данных о трендах и аналитики слушателей
- Доступ к данным треков, пользователей, плейлистов и альбомов как структурированным ресурсам

## Переменные окружения

### Опциональные
- `AUDIUS_API_KEY` - Ваш API ключ Audius
- `AUDIUS_API_SECRET` - Ваш секретный ключ API Audius
- `AUDIUS_ENVIRONMENT` - Настройка окружения (production, staging, development)
- `SERVER_NAME` - Имя MCP сервера
- `SERVER_VERSION` - Версия MCP сервера
- `AUDIO_STREAMING` - Включить/отключить аудио стриминг

## Примеры использования

```
Найди мне электронные треки с высоким BPM
```

```
Какие треки в жанре хип-хоп сейчас в тренде на этой неделе?
```

```
Порекомендуй исполнителей, похожих на [имя исполнителя]
```

```
Расскажи мне об исполнителе [имя]
```

```
Создай плейлист из энергичных электронных треков
```

## Ресурсы

- [GitHub Repository](https://github.com/glassBead-tc/audius-mcp-atris)

## Примечания

Версия 2.0.0+ использует исключительно STDIO транспорт. Сервер ориентирован на Model Context Protocol версии 2025-06-18. Поддерживает ресурсы через URI шаблоны (audius://track/{id}, audius://user/{id} и т.д.) и включает направляющие подсказки для рабочих процессов поиска, создания и анализа музыки.