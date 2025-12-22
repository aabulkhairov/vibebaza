---
title: Kaggle MCP сервер
description: MCP сервер для бесшовной интеграции с Kaggle API, позволяющий взаимодействовать с соревнованиями, датасетами, ядрами и моделями Kaggle через совместимые с MCP клиенты.
tags:
- API
- AI
- Analytics
- Integration
- Productivity
author: Seif-Sameh
featured: false
---

MCP сервер для бесшовной интеграции с Kaggle API, позволяющий взаимодействовать с соревнованиями, датасетами, ядрами и моделями Kaggle через совместимые с MCP клиенты.

## Установка

### Из исходного кода

```bash
git clone https://github.com/Seif-Sameh/Kaggle-mcp.git
cd Kaggle-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "kaggle": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/Kaggle-mcp",
        "run",
        "kaggle_mcp/server.py"
      ],
      "env":{
          "KAGGLE_USERNAME": "YOUR_KAGGLE_USERNAME",
          "KAGGLE_API_KEY": "YOUR_KAGGLE_API_KEY"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `competitions_list` | Список и поиск доступных соревнований |
| `competition_list_files` | Список всех файлов в соревновании |
| `competition_download_file` | Скачивание конкретного файла соревнования |
| `competition_download_files` | Скачивание всех файлов соревнования |
| `competition_submit` | Отправка предсказаний в соревнование |
| `competition_submissions` | Просмотр истории ваших отправок |
| `competition_leaderboard_view` | Просмотр таблицы лидеров соревнования |
| `competition_leaderboard_download` | Скачивание данных таблицы лидеров |
| `datasets_list` | Поиск и фильтрация датасетов |
| `dataset_metadata` | Получение метаданных датасета |
| `dataset_list_files` | Список файлов в датасете |
| `dataset_status` | Проверка статуса обработки датасета |
| `dataset_download_file` | Скачивание конкретного файла датасета |
| `dataset_download_files` | Скачивание всех файлов датасета |
| `dataset_create` | Создание нового датасета |

## Возможности

- Соревнования: список, скачивание файлов, отправка решений, просмотр таблиц лидеров и истории отправок
- Датасеты: поиск, скачивание, создание и управление датасетами с контролем версий
- Ядра: список, отправка, получение и управление Kaggle блокнотами и скриптами
- Модели: создание, обновление и управление ML моделями и экземплярами с полным контролем версий

## Переменные окружения

### Обязательные
- `KAGGLE_USERNAME` - Ваше имя пользователя Kaggle для аутентификации API
- `KAGGLE_API_KEY` - Ваш API ключ Kaggle для аутентификации

## Примеры использования

```
List the latest Kaggle competitions
```

```
Download the Titanic dataset
```

```
Show me my recent competition submissions
```

```
Search for NLP datasets
```

```
List active Kaggle competitions about computer vision
```

## Ресурсы

- [GitHub Repository](https://github.com/Seif-Sameh/Kaggle-mcp)

## Примечания

Требует Python 3.10 или выше и аккаунт Kaggle с учетными данными API. Может быть запущен автономно с командой kaggle-mcp или python -m kaggle_mcp.