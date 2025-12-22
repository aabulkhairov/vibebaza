---
title: FlightRadar24 MCP сервер
description: MCP сервер для Claude Desktop, который помогает отслеживать полёты в режиме реального времени используя данные Flightradar24. Идеально подходит для энтузиастов авиации, планировщиков путешествий или всех, кому интересно узнать о полётах над головой.
tags:
- API
- Monitoring
- Analytics
- Integration
author: sunsetcoder
featured: false
---

MCP сервер для Claude Desktop, который помогает отслеживать полёты в режиме реального времени используя данные Flightradar24. Идеально подходит для энтузиастов авиации, планировщиков путешествий или всех, кому интересно узнать о полётах над головой.

## Установка

### Из исходного кода

```bash
git clone https://github.com/sunsetcoder/flightradar24-mcp-server.git
cd flightradar24-mcp-server
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "flightradar24-server": {
      "command": "node",
      "args": [
        "/Users/<username>/<FULL_PATH...>/flightradar24-mcp-server/dist/index.js"
      ],
      "env": {
        "FR24_API_KEY": "your_api_key_here",
        "FR24_API_URL": "https://fr24api.flightradar24.com"
      }
    }
  }
}
```

## Возможности

- Отслеживание любого полёта в режиме реального времени
- Получение времени прибытия и отправления для конкретных рейсов
- Просмотр статуса рейсов в аэропорту
- Мониторинг экстренных рейсов

## Переменные окружения

### Обязательные
- `FR24_API_KEY` - Ваш API ключ Flightradar24 для доступа к данным о полётах
- `FR24_API_URL` - URL эндпоинта Flightradar24 API

## Примеры использования

```
Какое время прибытия у рейса United Airlines UA123?
```

```
Покажи мне все рейсы в SFO сейчас
```

```
Есть ли экстренные рейсы в этом районе?
```

```
Покажи все международные рейсы, прибывающие в SFO в следующие 2 часа
```

```
Сколько коммерческих рейсов сейчас летит над Тихим океаном?
```

## Ресурсы

- [GitHub Repository](https://github.com/sunsetcoder/flightradar24-mcp-server)

## Примечания

Требуется подписка на Flightradar24 API для доступа к данным о полётах. Убедитесь, что используете полный абсолютный путь в файле конфигурации и перезапустите Claude Desktop после внесения изменений.