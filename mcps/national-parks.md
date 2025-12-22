---
title: National Parks MCP сервер
description: MCP сервер для API Службы национальных парков (NPS), предоставляющий актуальную информацию о национальных парках США, включая детали парков, уведомления и активности.
tags:
- API
- Search
- Analytics
- Productivity
- Integration
author: Community
featured: false
---

MCP сервер для API Службы национальных парков (NPS), предоставляющий актуальную информацию о национальных парках США, включая детали парков, уведомления и активности.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @KyrieTangSheng/mcp-server-nationalparks --client claude
```

### NPX

```bash
npx -y mcp-server-nationalparks
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "nationalparks": {
      "command": "npx",
      "args": ["-y", "mcp-server-nationalparks"],
      "env": {
        "NPS_API_KEY": "YOUR_NPS_API_KEY"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `findParks` | Поиск национальных парков по различным критериям, включая штат, активности и поисковые термины |
| `getParkDetails` | Получение полной информации о конкретном национальном парке, включая описания, часы работы, сборы... |
| `getAlerts` | Получение текущих уведомлений для национальных парков, включая закрытия, опасности и важную информацию |
| `getVisitorCenters` | Получение информации о центрах для посетителей и их часах работы |
| `getCampgrounds` | Получение информации о доступных кемпингах и их удобствах |
| `getEvents` | Поиск предстоящих событий в парках |

## Возможности

- Поиск парков по штатам, активностям и ключевым словам
- Получение детальной информации о парках, включая сборы и часы работы
- Проверка текущих уведомлений и закрытий
- Поиск центров для посетителей с данными о местоположении и контактах
- Обнаружение кемпингов с информацией об удобствах и бронировании
- Просмотр предстоящих событий в парках с датами и описаниями
- Поддержка пагинации и фильтрации для всех инструментов
- Данные в реальном времени от API Службы национальных парков

## Переменные окружения

### Обязательные
- `NPS_API_KEY` - API ключ с портала разработчиков Службы национальных парков для аутентификации запросов

## Примеры использования

```
Tell me about national parks in Colorado.
```

```
What's the entrance fee for Yellowstone National Park?
```

```
Are there any closures or alerts at Yosemite right now?
```

```
What visitor centers are available at Grand Canyon National Park?
```

```
Are there any campgrounds with electrical hookups in Zion National Park?
```

## Ресурсы

- [GitHub Repository](https://github.com/KyrieTangSheng/mcp-server-nationalparks)

## Примечания

Требует бесплатный API ключ с портала разработчиков Службы национальных парков. Сервер включает приложение с популярными кодами парков для удобного справочника. Лицензируется под MIT License.