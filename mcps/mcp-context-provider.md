---
title: MCP Context Provider MCP сервер
description: Статический MCP сервер, который предоставляет AI моделям постоянный контекст для инструментов, правила и синтаксические предпочтения, сохраняющиеся между сессиями чата, предотвращая потерю контекста и обеспечивая автоматические исправления.
tags:
- Productivity
- AI
- Code
- DevOps
- Integration
author: doobidoo
featured: false
---

Статический MCP сервер, который предоставляет AI моделям постоянный контекст для инструментов, правила и синтаксические предпочтения, сохраняющиеся между сессиями чата, предотвращая потерю контекста и обеспечивая автоматические исправления.

## Установка

### Автоматическая установка (Unix/Linux/macOS)

```bash
git clone https://github.com/doobidoo/MCP-Context-Provider.git
cd MCP-Context-Provider
./scripts/install.sh
```

### Автоматическая установка (Windows)

```bash
git clone https://github.com/doobidoo/MCP-Context-Provider.git
cd MCP-Context-Provider
.\scripts\install.bat
```

### Ручная установка из DXT

```bash
npm install -g @anthropic-ai/dxt
wget https://github.com/doobidoo/MCP-Context-Provider/raw/main/mcp-context-provider-1.2.1.dxt
dxt unpack mcp-context-provider-1.2.1.dxt ~/mcp-context-provider
cd ~/mcp-context-provider
python -m venv venv
source venv/bin/activate
pip install mcp>=1.9.4
```

### Из исходного кода

```bash
git clone https://github.com/doobidoo/MCP-Context-Provider.git
cd MCP-Context-Provider
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop (виртуальное окружение)

```json
{
  "mcpServers": {
    "context-provider": {
      "command": "/path/to/mcp-context-provider/venv/bin/python",
      "args": ["/path/to/mcp-context-provider/context_provider_server.py"],
      "env": {
        "CONTEXT_CONFIG_DIR": "/path/to/mcp-context-provider/contexts",
        "AUTO_LOAD_CONTEXTS": "true"
      }
    }
  }
}
```

### Claude Desktop (системный Python)

```json
{
  "mcpServers": {
    "context-provider": {
      "command": "python",
      "args": ["context_provider_server.py"],
      "cwd": "/path/to/MCP-Context-Provider",
      "env": {
        "CONTEXT_CONFIG_DIR": "./contexts",
        "AUTO_LOAD_CONTEXTS": "true"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_tool_context` | Получить правила контекста для конкретного инструмента |
| `get_syntax_rules` | Получить правила преобразования синтаксиса |
| `list_available_contexts` | Показать все загруженные категории контекста |
| `apply_auto_corrections` | Применить автоматические исправления синтаксиса |
| `execute_session_initialization` | Инициализировать сессию с интеграцией сервиса памяти |
| `get_session_status` | Получить детальный статус инициализации сессии |
| `create_context_file` | Создать новые файлы контекста динамически с валидацией |
| `update_context_rules` | Обновить существующие правила контекста с резервным копированием и валидацией |
| `add_context_pattern` | Добавить паттерны для автоматического срабатывания секций для интеграции с памятью |
| `analyze_context_effectiveness` | Анализировать эффективность контекста с insights на основе памяти |
| `suggest_context_optimizations` | Генерировать глобальные предложения по оптимизации на основе паттернов использования |
| `get_proactive_suggestions` | Предоставить проактивные предложения контекста для улучшения рабочего процесса |
| `auto_optimize_context` | Автоматически оптимизировать контексты на основе рекомендаций движка обучения |

## Возможности

- Постоянный контекст, который сохраняется при перезапуске Claude Desktop
- Автоматическое внедрение специфических правил для инструментов и синтаксических предпочтений
- Правила контекста для DokuWiki, Terraform, Azure, Git и других инструментов
- Автоматические преобразования синтаксиса (например, Markdown → DokuWiki)
- Управление контекстом с версионным контролем для корпоративного использования
- Динамическое создание и управление файлами контекста
- Интеллектуальная система обучения, анализирующая эффективность контекста
- Интеграция с сервисом памяти для постоянных данных обучения
- Автоматическая оптимизация контекста на основе паттернов использования
- Проактивные предложения для улучшения рабочего процесса

## Переменные окружения

### Обязательные
- `CONTEXT_CONFIG_DIR` - Путь к директории с файлами конфигурации контекста

### Опциональные
- `AUTO_LOAD_CONTEXTS` - Включить автоматическую загрузку файлов контекста при запуске
- `ENVIRONMENT` - Загрузка контекста для конкретной среды (например, 'prod')

## Примеры использования

```
Получить правила синтаксиса DokuWiki для форматирования документации
```

```
Применить автоматические исправления синтаксиса для конвертации Markdown в формат DokuWiki
```

```
Показать все доступные контексты инструментов и их категории
```

```
Получить соглашения по именованию Terraform и лучшие практики
```

```
Применить правила соответствия именования ресурсов Azure автоматически
```

## Ресурсы

- [GitHub Repository](https://github.com/doobidoo/MCP-Context-Provider)

## Примечания

Сервер автоматически загружает файлы контекста из директории /contexts и поддерживает DokuWiki, Terraform, Azure, Git и общие предпочтения. Версия 1.6.0+ включает интеллектуальную систему обучения, которая требует интеграции с mcp-memory-service для продвинутых возможностей. Файлы контекста следуют JSON структуре с категориями инструментов, правилами синтаксиса, предпочтениями и автоматическими исправлениями.