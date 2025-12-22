---
title: Star Wars MCP сервер
description: MCP сервер для SWAPI Star Wars API, который демонстрирует, как MCP сервер может взаимодействовать с API, предоставляя доступ к персонажам, планетам, фильмам, видам, транспортным средствам и звездолетам Star Wars со встроенным кэшированием и пагинацией.
tags:
- API
- Integration
- Media
- Search
author: Community
featured: false
---

MCP сервер для SWAPI Star Wars API, который демонстрирует, как MCP сервер может взаимодействовать с API, предоставляя доступ к персонажам, планетам, фильмам, видам, транспортным средствам и звездолетам Star Wars со встроенным кэшированием и пагинацией.

## Установка

### NPX

```bash
npx -y @johnpapa/mcp-starwars
```

### Smithery CLI

```bash
npx -y @smithery/cli install @johnpapa/mcp-starwars --client claude
```

### VS Code Command Line

```bash
code --add-mcp '{"name":"starwars","command":"npx","args":["-y","@johnpapa/mcp-starwars"],"env":{}}'
```

### Из исходного кода

```bash
git clone https://github.com/johnpapa/-mcp-starwars
npm install
npm run build
npx @modelcontextprotocol/inspector node build/index.js
```

## Конфигурация

### VS Code Settings JSON

```json
"mcp": {
  "servers": {
    "starwars": {
      "command": "npx",
      "args": ["-y", "@johnpapa/mcp-starwars"],
      "env": {}
    }
  }
},
"chat.mcp.discovery.enabled": true
```

### VS Code MCP JSON

```json
{
  "inputs": [],
  "servers": {
    "mcp-starwars": {
      "command": "npx",
      "args": [
        "-y",
        "@johnpapa/mcp-starwars"
      ],
      "env": {}
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_people` | Список персонажей Star Wars с автоматической пагинацией и опциональным поиском |
| `get_person_by_id` | Получение детальной информации о конкретном персонаже Star Wars по ID |
| `get_planets` | Список планет Star Wars с автоматической пагинацией и опциональным поиском |
| `get_planet_by_id` | Получение детальной информации о конкретной планете Star Wars по ID |
| `get_films` | Список фильмов Star Wars с автоматической пагинацией и опциональным поиском |
| `get_film_by_id` | Получение детальной информации о конкретном фильме Star Wars по ID |
| `get_species_list` | Список видов Star Wars с автоматической пагинацией и опциональным поиском |
| `get_species_by_id` | Получение детальной информации о конкретном виде Star Wars по ID |
| `get_vehicles` | Список транспортных средств Star Wars с автоматической пагинацией и опциональным поиском |
| `get_vehicle_by_id` | Получение детальной информации о конкретном транспортном средстве Star Wars по ID |
| `get_starships` | Список звездолетов Star Wars с автоматической пагинацией и опциональным поиском |
| `get_starship_by_id` | Получение детальной информации о конкретном звездолете Star Wars по ID |
| `clear_cache` | Очистка кэша Star Wars API (частично или полностью) |
| `get_cache_stats` | Получение статистики об использовании кэша Star Wars API |

## Возможности

- Список персонажей Star Wars с опциональными фильтрами поиска и автоматической пагинацией
- Список планет, фильмов, видов, транспортных средств и звездолетов с возможностями поиска
- Получение детальной информации по ID для конкретных персонажей, планет, фильмов, видов, транспортных средств или звездолетов
- Автоматическая пагинация для бесшовного получения всех страниц данных одним API вызовом
- Встроенное кэширование для оптимизации производительности с интеллектуальным кэшированием ответов API
- Управление кэшем для очистки кэша и просмотра статистики кэша

## Ресурсы

- [GitHub Repository](https://github.com/johnpapa/mcp-starwars)

## Примечания

Все данные, используемые этим MCP сервером, получаются из документации SWAPI. Сервер требует Node.js >=20 и лицензирован под MIT. Доступны значки установки для VS Code, VS Code Insiders, с опциями как NPM, так и Docker.