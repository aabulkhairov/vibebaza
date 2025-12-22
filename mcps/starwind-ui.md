---
title: Starwind UI MCP сервер
description: TypeScript реализация MCP сервера для Starwind UI, которая предоставляет инструменты для помощи разработчикам в работе с компонентами Starwind UI при использовании AI инструментов как Claude, Windsurf и Cursor.
tags:
- Code
- Productivity
- Integration
- AI
- DevOps
author: Community
featured: false
install_command: npx -y @smithery/cli install @starwind-ui/starwind-ui-mcp --client
  claude
---

TypeScript реализация MCP сервера для Starwind UI, которая предоставляет инструменты для помощи разработчикам в работе с компонентами Starwind UI при использовании AI инструментов как Claude, Windsurf и Cursor.

## Установка

### NPX

```bash
npx -y @starwind-ui/mcp
```

### Smithery

```bash
npx -y @smithery/cli install @starwind-ui/starwind-ui-mcp --client claude
```

## Конфигурация

### Windsurf

```json
{
	"mcpServers": {
		"starwind-ui": {
			"command": "npx",
			"args": ["-y", "@starwind-ui/mcp"],
			"env": {}
		}
	}
}
```

### Cursor

```json
{
	"mcpServers": {
		"starwind-ui": {
			"command": "npx",
			"args": ["-y", "@starwind-ui/mcp"],
			"env": {}
		}
	}
}
```

### Claude Code

```json
{
	"mcpServers": {
		"starwind-ui": {
			"command": "npx",
			"args": ["-y", "@starwind-ui/mcp"],
			"env": {}
		}
	}
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `init_project` | Инициализирует новый проект Starwind UI |
| `install_component` | Генерирует команды установки для компонентов Starwind UI |
| `update_component` | Генерирует команды обновления для компонентов Starwind UI |
| `get_documentation` | Возвращает ссылки на документацию для компонентов Starwind UI и руководств |
| `fetch_llm_data` | Получает данные LLM с starwind.dev (с ограничением скорости и кэшированием) |
| `get_package_manager` | Определяет и возвращает информацию о текущем менеджере пакетов |

## Возможности

- Архитектура на основе инструментов - Модульный дизайн для простого добавления новых инструментов
- Инструмент документации Starwind UI - Доступ к ссылкам на документацию для компонентов Starwind UI
- Определение менеджера пакетов - Определение и использование подходящего менеджера пакетов (npm, yarn, pnpm)
- Получение данных LLM - Получение информации Starwind UI для LLM с кэшированием и ограничением скорости
- Реализация на TypeScript - Создан с TypeScript для лучшей типобезопасности и опыта разработчика
- Транспорт стандартного ввода-вывода - Использует stdio для связи с AI помощниками

## Ресурсы

- [GitHub Repository](https://github.com/Boston343/starwind-ui-mcp)

## Примечания

Предоставляет соответствующие команды, документацию и другую информацию, чтобы позволить LLM в полной мере использовать преимущества open source Astro компонентов Starwind UI. Включает бейдж оценки безопасности от MseeP.ai и верифицирован на платформе MseeP.