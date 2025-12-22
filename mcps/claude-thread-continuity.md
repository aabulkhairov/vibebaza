---
title: Claude Thread Continuity MCP сервер
description: Автоматически сохраняет и восстанавливает контекст разговора с Claude при достижении лимитов токенов, обеспечивая бесшовную непрерывность между сессиями с умной валидацией проектов для предотвращения фрагментации.
tags:
- Productivity
- Storage
- AI
- Integration
author: Community
featured: false
---

Автоматически сохраняет и восстанавливает контекст разговора с Claude при достижении лимитов токенов, обеспечивая бесшовную непрерывность между сессиями с умной валидацией проектов для предотвращения фрагментации.

## Установка

### Быстрый старт

```bash
# 1. Clone the repository
git clone https://github.com/peless/claude-thread-continuity.git
cd claude-thread-continuity

# 2. Install dependencies
pip install -r requirements.txt

# 3. Test the enhanced server
python3 test_server.py
```

### Из исходников

```bash
# Create permanent directory
mkdir -p ~/.mcp-servers/claude-continuity
cd ~/.mcp-servers/claude-continuity

# Copy files (or clone repo to this location)
# Place server.py and requirements.txt here
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "claude-continuity": {
      "command": "python3",
      "args": ["~/.mcp-servers/claude-continuity/server.py"],
      "env": {}
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `save_project_state` | Сохранение текущего состояния проекта с валидацией |
| `load_project_state` | Восстановление полного контекста проекта |
| `list_active_projects` | Просмотр всех отслеживаемых проектов |
| `get_project_summary` | Получение краткого обзора проекта |
| `validate_project_name` | Проверка на похожие имена проектов |
| `auto_save_checkpoint` | Срабатывает автоматически |

## Возможности

- Автоматическое сохранение состояния - Авто-сохранение контекста проекта во время разговоров
- Бесшовное восстановление - Мгновенное восстановление полного контекста при запуске новых потоков
- Умная валидация - Предотвращает фрагментацию проектов с интеллектуальной проверкой имен
- Приватность прежде всего - Все данные хранятся локально на вашей машине
- Нулевая конфигурация - Работает незаметно после настройки
- Умные триггеры - Авто-сохранение при изменении файлов, решениях, вехах
- Поддержка множественных проектов - Управление несколькими параллельными проектами
- Система анти-фрагментации - Нечеткое сопоставление имен с 70% порогом сходства
- Принудительное переопределение - Обход валидации когда действительно нужны разные проекты
- Настраиваемые пороги - Регулировка чувствительности под ваш рабочий процесс

## Примеры использования

```
save_project_state: project_name="my-web-app", current_focus="Setting up React components", technical_decisions=["Using TypeScript", "Vite for bundling"], next_actions=["Create header component", "Set up routing"]
```

```
validate_project_name: project_name="my-webapp", similarity_threshold=0.7
```

```
save_project_state: project_name="my-web-app-v2", force=true, current_focus="Starting version 2"
```

```
load_project_state: project_name="my-web-app"
```

```
list_active_projects
```

## Ресурсы

- [GitHub Repository](https://github.com/peless/claude-thread-continuity)

## Примечания

Состояния проектов хранятся локально в ~/.claude_states/ с автоматической ротацией резервных копий. Поддерживает Python 3.8+ и включает комплексный набор тестов. Идеально подходит для сложных проектов разработки, обучения и исследований, писательских проектов и отладки в нескольких сессиях.