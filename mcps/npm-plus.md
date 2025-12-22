---
title: NPM Plus MCP сервер
description: AI-powered управление JavaScript пакетами с проверкой безопасности, анализом бандлов и интеллектуальным управлением зависимостями для MCP-совместимых редакторов как Claude, Windsurf и Cursor.
tags:
- Code
- Security
- DevOps
- Analytics
- API
author: shacharsol
featured: false
---

AI-powered управление JavaScript пакетами с проверкой безопасности, анализом бандлов и интеллектуальным управлением зависимостями для MCP-совместимых редакторов как Claude, Windsurf и Cursor.

## Установка

### Хостинг сервис

```bash
{
  "mcpServers": {
    "npmplus-mcp": {
      "transport": "http",
      "url": "https://api.npmplus.dev/mcp"
    }
  }
}
```

### NPX

```bash
{
  "mcpServers": {
    "npmplus-mcp": {
      "command": "npx",
      "args": ["-y", "npmplus-mcp-server"]
    }
  }
}
```

### Из исходного кода

```bash
git clone https://github.com/shacharsol/js-package-manager-mcp.git
cd js-package-manager-mcp
npm install
npm run build
npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "npmplus-mcp": {
      "transport": "http",
      "url": "https://api.npmplus.dev/mcp"
    }
  }
}
```

### Windsurf Hosted

```json
{
  "mcpServers": {
    "npmplus-mcp": {
      "serverUrl": "https://api.npmplus.dev/mcp"
    }
  }
}
```

### Windsurf NPX

```json
{
  "mcp": {
    "servers": {
      "npmplus-mcp": {
        "command": "npx",
        "args": [
          "-y",
          "npmplus-mcp-server"
        ],
        "disabled": false
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "npmplus-mcp": {
      "command": "npx",
      "args": ["-y", "npmplus-mcp-server"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_packages` | Поиск в npm реестре с интеллектуальной оценкой |
| `package_info` | Получение детальной информации о пакете |
| `check_bundle_size` | Анализ размера бандла перед установкой |
| `download_stats` | Просмотр статистики загрузок и трендов |
| `check_license` | Проверка лицензионной информации пакета |
| `dependency_tree` | Визуализация связей зависимостей |
| `list_licenses` | Список всех лицензий проекта |
| `audit_dependencies` | Сканирование уязвимостей безопасности |
| `analyze_dependencies` | Обнаружение циклических зависимостей и проблем |
| `check_outdated` | Поиск устаревших пакетов |
| `clean_cache` | Очистка кэша пакетного менеджера |
| `check_vulnerability` | Проверка уязвимостей конкретного пакета |
| `install_packages` | Установка пакетов с интеллектуальной логикой повторов |
| `update_packages` | Обновление пакетов до последних версий |
| `remove_packages` | Удаление пакетов из проекта |

## Возможности

- Умное обнаружение пакетов с интеллектуальной оценкой релевантности
- Интеллектуальное управление пакетами для NPM, Yarn и pnpm
- Безопасность и соответствие с сканированием уязвимостей в реальном времени
- Продвинутая аналитика с анализом размера бандлов и визуализацией дерева зависимостей
- Автоматическое определение пакетного менеджера с логикой повторов
- Отслеживание и анализ соответствия лицензий
- Статистика загрузок и метрики популярности
- Обнаружение потерянных файлов
- Интеллектуальное кэширование с настраиваемыми TTL
- Ограничение частоты запросов для предотвращения API throttling

## Переменные окружения

### Опциональные
- `ENABLE_ANALYTICS` - Включение логирования аналитики для self-hosted деплоев
- `ANALYTICS_SALT` - Случайная соль для хеширования данных аналитики

## Примеры использования

```
Search for React testing libraries
```

```
What's the current version of React?
```

```
Install express and cors packages
```

```
Show me popular authentication libraries
```

```
What's the bundle size of lodash?
```

## Ресурсы

- [GitHub Repository](https://github.com/shacharsol/js-package-manager-mcp)

## Примечания

Production-ready MCP сервер с 16/16 полностью функциональными инструментами. Поддерживает как хостинг сервис (рекомендуется), так и self-hosting. Работает с Claude Desktop, Windsurf, Cursor, VS Code + Cline. Все инструменты поддерживают как относительные (.), так и абсолютные пути. Улучшен интеллектуальной логикой повторов и надежной обработкой ошибок.