---
title: Tensorboard Query MCP сервер
description: MCP сервер для запроса и анализа файлов событий TensorBoard без необходимости запущенного TensorBoard сервера, обеспечивающий программный доступ к метрикам обучения и автоматизированный анализ.
tags:
- Analytics
- Monitoring
- AI
- DevOps
- Code
author: Alir3z4
featured: false
---

MCP сервер для запроса и анализа файлов событий TensorBoard без необходимости запущенного TensorBoard сервера, обеспечивающий программный доступ к метрикам обучения и автоматизированный анализ.

## Установка

### Из PyPI

```bash
pip install tb-query
```

### Из исходного кода

```bash
git clone https://github.com/Alir3z4/tb-query.git
cd tb-query
pip install -e .
```

### MCP сервер

```bash
tb-query-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "tb-query": {
      "command": "tb-query-mcp",
      "env": {
        "TB_QUERY_EVENTS_PATH": "/path/to/your/tensorboard/logs"
      }
    }
  }
}
```

### Cline (VS Code расширение)

```json
{
  "mcpServers": {
    "tb-query": {
      "command": "tb-query-mcp",
      "env": {
        "TB_QUERY_EVENTS_PATH": "/path/to/your/tensorboard/logs"
      }
    }
  }
}
```

### Zed Editor

```json
{
  "context_servers": {
    "tb-query": {
      "command": "tb-query-mcp",
      "env": {
        "TB_QUERY_EVENTS_PATH": "/path/to/your/tensorboard/logs"
      }
    }
  }
}
```

### Continue (VS Code расширение)

```json
{
  "mcpServers": [
    {
      "name": "tb-query",
      "command": "tb-query-mcp",
      "env": {
        "TB_QUERY_EVENTS_PATH": "/path/to/your/tensorboard/logs"
      }
    }
  ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `query` | Запрос скалярных данных из файла событий TensorBoard с опциональной фильтрацией по тегам и шагам |
| `list_tags` | Получить все доступные скалярные теги с опциональной фильтрацией |
| `find_events` | Найти все файлы событий TensorBoard в директории и поддиректориях |
| `tag_steps` | Получить номера шагов для указанных тегов |
| `tag_stats` | Получить статистические показатели (мин, макс, среднее, стандартное отклонение) для указанных тегов |
| `correlation` | Вычислить корреляции Пирсона между скалярными тегами |

## Возможности

- Запрос скалярных данных с фильтрацией по шагам и тегам
- Поиск всех файлов событий TensorBoard в дереве директорий
- Вывод доступных скалярных тегов с опциональной фильтрацией
- Вычисление статистики (мин, макс, среднее, стандартное отклонение) для конкретных тегов
- Расчет корреляций между различными скалярными метриками
- CLI интерфейс для использования из командной строки
- MCP сервер для интеграции с AI помощниками для кодирования
- Прямой доступ к файлам событий TensorBoard без веб-сервера

## Переменные окружения

### Опциональные
- `TB_QUERY_EVENTS_PATH` - Директория по умолчанию для файлов событий, включает ресурс event_files

## Примеры использования

```
Проанализируй последний запуск обучения в моей папке с логами
```

```
Какая корреляция между loss и learning rate?
```

```
Покажи статистику для метрик точности
```

```
Сравни последние 100 шагов train и validation loss
```

## Ресурсы

- [GitHub Repository](https://github.com/Alir3z4/tb-query)

## Примечания

Требует Python >= 3.11 и зависимости: tensorboard, fastmcp, pandas. Предоставляет как CLI команды, так и Python API для прямой интеграции. Когда установлена переменная TB_QUERY_EVENTS_PATH, предоставляет ресурс event_files для автоматического обнаружения файлов.