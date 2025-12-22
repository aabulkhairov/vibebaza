---
title: LottieFiles MCP сервер
description: Model Context Protocol (MCP) сервер для поиска и получения Lottie анимаций из LottieFiles.
tags:
- Search
- Media
- API
author: Community
featured: false
---

Model Context Protocol (MCP) сервер для поиска и получения Lottie анимаций из LottieFiles.

## Установка

### Smithery

```bash
npx -y smithery install mcp-server-lottiefiles --client claude
```

### Ручная установка

```bash
npm install
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_animations` | Поиск Lottie анимаций по ключевым словам с поддержкой пагинации |
| `get_animation_details` | Получение детальной информации о конкретной Lottie анимации по ID |
| `get_popular_animations` | Получение списка популярных Lottie анимаций с поддержкой пагинации |

## Возможности

- Поиск Lottie анимаций
- Получение деталей анимации
- Получение списка популярных анимаций

## Ресурсы

- [GitHub Repository](https://github.com/junmer/mcp-server-lottiefiles)

## Примечания

Запустите сервер командой 'npm start' и подключитесь с помощью MCP клиента. Сборка выполняется командой 'npm run build'. Лицензия MIT.