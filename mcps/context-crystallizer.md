---
title: Context Crystallizer MCP сервер
description: Инструмент для AI Context Engineering, который трансформирует большие репозитории в кристаллизованные, понятные для ИИ знания через систематический анализ и оптимизацию, создавая поисковые базы знаний для AI агентов.
tags:
- AI
- Code
- Analytics
- Productivity
- API
author: Community
featured: false
---

Инструмент для AI Context Engineering, который трансформирует большие репозитории в кристаллизованные, понятные для ИИ знания через систематический анализ и оптимизацию, создавая поисковые базы знаний для AI агентов.

## Установка

### NPM Global

```bash
npm install -g context-crystallizer
```

### NPX

```bash
npx context-crystallizer
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "context-crystallizer": {
      "command": "npx",
      "args": ["context-crystallizer"],
      "cwd": "/path/to/your/project"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_crystallization_guidance` | Получить комплексное руководство по анализу с шаблонами и стандартами качества |
| `init_crystallization` | Инициализировать кристаллизацию репозитория, сканировать и подготавливать файлы |
| `get_next_file_to_crystallize` | Получить следующий файл для AI анализа в процессе кристаллизации |
| `store_crystallized_context` | Сохранить сгенерированные AI знания и кристаллизованный контекст |
| `get_crystallization_progress` | Мониторить статус и прогресс кристаллизации |
| `search_crystallized_contexts` | Найти релевантные знания по функциональности или ключевым словам |
| `get_crystallized_bundle` | Объединить несколько контекстов в рамках лимитов токенов |
| `find_related_crystallized_contexts` | Обнаружить связи кода и зависимости |
| `search_by_complexity` | Найти контексты по уровню сложности (низкий, средний, высокий) |
| `validate_crystallization_quality` | Оценить качество контекста с метриками полноты и читаемости |
| `update_crystallized_contexts` | Обновить контексты для измененных файлов и поддержать актуальность |

## Возможности

- Поиск по функциональности с запросами на естественном языке
- Соотношение сжатия 5:1 (исходный код к кристаллизованному контексту)
- Формат, оптимизированный для AI и структурированный для потребления LLM
- Умная сборка, объединяющая несколько контекстов в рамках лимитов токенов
- Автоматическое соблюдение .gitignore и фильтрация бинарных файлов
- Создание поисковой базы кристаллизованных знаний
- Мониторинг прогресса и валидация качества
- Обнаружение связей между файлами кода
- Фильтрация контекста по сложности

## Примеры использования

```
I need to understand how authentication works in this massive project
```

```
What files depend on the authentication system?
```

```
How does authentication work in this app?
```

```
Show me how the payment system works
```

```
What depends on this Auth.tsx file?
```

## Ресурсы

- [GitHub Repository](https://github.com/hubertciebiada/context-crystallizer)

## Примечания

Вдохновлен AI Distiller, фокусируется на том, чтобы AI агенты генерировали комплексные кристаллизованные контексты о функциональности, паттернах и связях. Сервер должен запускаться из корневой директории проекта для интеграции с AI агентами. Кристаллизованные контексты сохраняются в директории .context-crystallizer/.