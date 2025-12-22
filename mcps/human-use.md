---
title: Human-use MCP сервер
description: MCP сервер, который соединяет AI агентов с человеческим интеллектом через Rapidata API, позволяя искусственному интеллекту задавать реальным людям вопросы и получать обратную связь по различным задачам.
tags:
- AI
- API
- Integration
- Analytics
- Productivity
author: Community
featured: false
---

MCP сервер, который соединяет AI агентов с человеческим интеллектом через Rapidata API, позволяя искусственному интеллекту задавать реальным людям вопросы и получать обратную связь по различным задачам.

## Установка

### Из исходного кода

```bash
git clone https://github.com/RapidataAI/human-use.git
# Install uv
curl -LsSf https://astral.sh/uv/install.sh | sh
# On Windows: powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
uv venv
source .venv/bin/activate
uv sync
```

### Запуск приложения

```bash
streamlit run app.py
```

## Конфигурация

### Cursor

```json
{
    "mcpServers": {
        "human-use": {
            "command": "uv",
            "args": [
                "--directory",
                "YOUR_ABSOLUTE_PATH_HERE",
                "run",
                "rapidata_human_api.py"
            ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_free_text_responses` | Попросит реальных людей предоставить короткие текстовые ответы на вопрос |
| `get_human_image_classification` | Попросит реальных людей классифицировать изображения в директории |
| `get_human_image_ranking` | Попросит реальных людей ранжировать изображения в директории |
| `get_human_text_comparison` | Попросит реальных людей сравнить два текста и выбрать, какой из них лучше |

## Возможности

- Соединение AI агентов с человеческим интеллектом
- Получение обратной связи от людей на текстовые ответы
- Классификация изображений силами людей
- Ранжирование изображений силами людей
- Сравнение текстов людьми
- Доступна хостинговая версия на chat.rapidata.ai
- Интерфейс на основе кастомного Streamlit приложения

## Примеры использования

```
Coming up with a cool car design
```

```
Finding the best slogan
```

```
Function naming
```

```
Ranking different image generation models
```

## Ресурсы

- [GitHub Repository](https://github.com/RapidataAI/human-use)

## Примечания

Пути должны быть АБСОЛЮТНЫМИ путями. Если возникают проблемы с зависимостями, убедитесь, что 'which python' и 'which streamlit' указывают на одинаковый путь. Приложение включает кастомный Streamlit интерфейс, созданный из-за проблем с другими MCP клиентами, такими как Claude desktop app. Для поддержки обращайтесь на info@rapidata.ai.