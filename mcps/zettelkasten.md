---
title: Zettelkasten MCP сервер
description: AI-система управления знаниями по методу Zettelkasten, которая помогает фиксировать,
  совершенствовать и связывать атомарные идеи с помощью CEQRC рабочего процесса (Capture→Explain→Question→Refine→Connect)
  с интеллектуальным связыванием и доступом через несколько интерфейсов.
tags:
- AI
- Productivity
- Search
- Database
- API
author: joshylchen
featured: false
---

AI-система управления знаниями по методу Zettelkasten, которая помогает фиксировать, совершенствовать и связывать атомарные идеи с помощью CEQRC рабочего процесса (Capture→Explain→Question→Refine→Connect) с интеллектуальным связыванием и доступом через несколько интерфейсов.

## Установка

### Из исходного кода

```bash
git clone https://github.com/joshylchen/zettelkasten
cd zettelkasten
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
mkdir -p data/notes data/db
```

### Настройка MCP

```bash
python setup_mcp.py
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "zettelkasten": {
      "command": "python", 
      "args": ["path/to/mcp_server.py"],
      "env": {"OPENAI_API_KEY": "your_key_here"}
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `zk_create_note` | Создание атомарных заметок с AI-резюме |
| `zk_search_notes` | Полнотекстовый поиск с синтаксисом FTS5 |
| `zk_get_note` | Получение заметок с метаданными и обратными ссылками |
| `zk_run_ceqrc_workflow` | Выполнение AI-процесса обучения |
| `zk_suggest_links` | Обнаружение связей между заметками |
| `zk_create_link` | Создание типизированных связей (supports, refines, extends, и т.д.) |
| `zk_generate_summary` | Генерация AI-резюме для любого текста |

## Возможности

- Атомарные заметки с уникальными ID, заголовками, телом и AI-резюме
- Полнотекстовый поиск с помощью SQLite FTS5 с поиском по близости и фразовым соответствием
- AI-процесс CEQRC для улучшения знаний
- Двунаправленная связь с типизированными отношениями
- Несколько интерфейсов: CLI, REST API, Streamlit UI и MCP
- Обычные Markdown файлы с YAML frontmatter как источник истины
- Умное резюмирование с настраиваемыми ограничениями длины
- Автоматическое обнаружение связей между связанными заметками
- Фильтрация и организация по тегам
- Интеграция техники Фейнмана для понимания концепций

## Переменные окружения

### Опциональные
- `ZK_NOTES_DIR` - Директория для хранения файлов заметок
- `ZK_DB_PATH` - Путь к файлу базы данных SQLite
- `ZK_HOST` - Адрес хоста сервера
- `ZK_PORT` - Номер порта сервера
- `OPENAI_API_KEY` - OpenAI API ключ для AI функций
- `ZK_LLM_PROVIDER` - LLM провайдер (openai или stub)
- `ZK_SUMMARY_MAX_LENGTH` - Максимальная длина AI-резюме
- `ZK_STREAMLIT_PORT` - Порт для Streamlit UI

## Примеры использования

```
Создание заметки об основах машинного обучения с AI-резюме и тегами
```

```
Поиск всех заметок, связанных с 'искусственным интеллектом' с полнотекстовым поиском
```

```
Запуск CEQRC процесса для заметки для улучшения и совершенствования содержимого
```

```
Поиск связей между заметками на похожие темы с помощью AI-обнаружения ссылок
```

```
Генерация вопросов для проверки понимания сложной концепции с использованием техники Фейнмана
```

## Ресурсы

- [GitHub Repository](https://github.com/joshylchen/zettelkasten)

## Примечания

Система реализует метод Zettelkasten с AI-улучшениями, сохраняя заметки как Markdown файлы с YAML frontmatter. Включает подробную документацию в папке docs/ и поддерживает как OpenAI, так и stub LLM провайдеры для тестирования.