---
title: NS Travel Information MCP сервер
description: Подключает AI-ассистентов к реальной информации о поездках NS (Nederlandse Spoorwegen), предоставляя расписания голландских железных дорог, данные о задержках, ценах и деталях станций.
tags:
- API
- Integration
- Analytics
- Productivity
author: r-huijts
featured: false
install_command: npx -y @smithery/cli install ns-server --client claude
---

Подключает AI-ассистентов к реальной информации о поездках NS (Nederlandse Spoorwegen), предоставляя расписания голландских железных дорог, данные о задержках, ценах и деталях станций.

## Установка

### NPX

```bash
npx -y ns-mcp-server
```

### Smithery

```bash
npx -y @smithery/cli install ns-server --client claude
```

### Из исходного кода

```bash
git clone [repository]
npm install
cp .env.example .env
# Add NS_API_KEY to .env file
```

## Конфигурация

### Claude Desktop (NPM)

```json
{
  "mcpServers": {
    "ns-server": {
      "command": "npx",
      "args": [
        "-y",
        "ns-mcp-server"
      ],
      "env": {
        "NS_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Claude Desktop (из исходного кода)

```json
{
  "mcpServers": {
    "ns-server": {
      "command": "node",
      "args": [
        "/path/to/ns-server/build/index.js"
      ],
      "env": {
        "NS_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Возможности

- Информация об отправлениях и прибытиях в реальном времени с номерами платформ и задержками
- Планирование поездок с оптимальными маршрутами и пересадками
- Обновления о сервисе, включая сбои и технические работы
- Цены на билеты для разных классов и групповых бронирований
- Информация о станциях, включая удобства, доступность и наличие OV-fiets
- Поддержка нескольких языков (голландский и английский)
- Гибкий поиск по названию станции, коду или UIC идентификатору
- Отслеживание статуса в реальном времени для изменений, задержек и отмен

## Переменные окружения

### Обязательные
- `NS_API_KEY` - Ваш ключ NS API (обязательно)

## Примеры использования

```
Is my usual 8:15 train from Almere to Amsterdam running on time?
```

```
Are there any delays on the Rotterdam-Den Haag route today?
```

```
What's the best alternative route to Utrecht if there's maintenance on the direct line?
```

```
Which train should I take to arrive at my office in Amsterdam Zuid before 9 AM?
```

```
Which route to Amsterdam has the fewest transfers with a stroller?
```

## Ресурсы

- [GitHub Repository](https://github.com/r-huijts/ns-mcp-server)

## Примечания

Требуется ключ API из NS API Portal (https://apiportal.ns.nl/). После изменения конфигурации перезапустите Claude Desktop, чтобы изменения вступили в силу.