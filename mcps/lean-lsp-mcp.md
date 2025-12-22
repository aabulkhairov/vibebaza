---
title: lean-lsp MCP сервер
description: MCP сервер, который обеспечивает взаимодействие агентов с Lean theorem prover через Language Server Protocol, предоставляя инструменты для LLM агентов для понимания, анализа и работы с Lean проектами.
tags:
- Code
- AI
- Search
- Analytics
- Productivity
author: Community
featured: false
install_command: claude mcp add lean-lsp uvx lean-lsp-mcp
---

MCP сервер, который обеспечивает взаимодействие агентов с Lean theorem prover через Language Server Protocol, предоставляя инструменты для LLM агентов для понимания, анализа и работы с Lean проектами.

## Установка

### UV

```bash
uvx lean-lsp-mcp
```

### Установить UV

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Собрать проект

```bash
lake build
```

### Установить Ripgrep

```bash
Install ripgrep (rg) and make sure it is available in your PATH
```

## Конфигурация

### VSCode

```json
{
    "servers": {
        "lean-lsp": {
            "type": "stdio",
            "command": "uvx",
            "args": [
                "lean-lsp-mcp"
            ]
        }
    }
}
```

### VSCode WSL2

```json
{
    "servers": {
        "lean-lsp": {
            "type": "stdio",
            "command": "wsl.exe",
            "args": [
                "uvx",
                "lean-lsp-mcp"
            ]
        }
    }
}
```

### Cursor

```json
{
    "mcpServers": {
        "lean-lsp": {
            "command": "uvx",
            "args": ["lean-lsp-mcp"]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `lean_file_outline` | Получить краткую структуру Lean файла с импортами и объявлениями с сигнатурами типов |
| `lean_file_contents` | Получить содержимое Lean файла, опционально с аннотациями номеров строк (УСТАРЕЛО) |
| `lean_diagnostic_messages` | Получить все диагностические сообщения для Lean файла, включая информацию, предупреждения и ошибки |
| `lean_goal` | Получить цель доказательства в определенном месте Lean файла |
| `lean_term_goal` | Получить цель терма в определенной позиции Lean файла |
| `lean_hover_info` | Получить информацию при наведении для символов, термов и выражений в Lean файле |
| `lean_declaration_file` | Получить содержимое файла, где объявлен символ или терм |
| `lean_completions` | Найти доступные идентификаторы или предложения импорта в определенной позиции |
| `lean_run_code` | Запустить/скомпилировать независимый фрагмент/файл Lean кода и вернуть результат или сообщение об ошибке |
| `lean_multi_attempt` | Попробовать несколько фрагментов lean кода на строке и вернуть состояние цели и диагностику |
| `lean_local_search` | Искать определения и теоремы Lean в локальном проекте Lean и stdlib |
| `lean_leansearch` | Искать теоремы в Mathlib используя leansearch.net (поиск на естественном языке) |
| `lean_loogle` | Искать определения и теоремы Lean используя loogle.lean-lang.org |
| `lean_leanfinder` | Семантический поиск теорем Mathlib используя Lean Finder |
| `lean_state_search` | Искать применимые теоремы для текущей цели доказательства используя premise-search.com |

## Возможности

- Богатое взаимодействие с Lean: Доступ к диагностике, состояниям целей, информации о термах, документации при наведении и многому другому
- Внешние инструменты поиска: Используйте LeanSearch, Loogle, Lean Finder, Lean Hammer и Lean State Search для поиска релевантных теорем
- Простая настройка: Простая конфигурация для различных клиентов, включая VSCode, Cursor и Claude Code
- Возможности локального поиска с интеграцией ripgrep
- Многопопыточная проверка доказательств
- Завершение кода и автоподсказки

## Переменные окружения

### Опциональные
- `LEAN_STATE_SEARCH_URL` - URL для самостоятельно размещенного экземпляра Lean State Search
- `LEAN_HAMMER_URL` - URL для самостоятельно размещенного экземпляра Lean Hammer

## Примеры использования

```
bijective map from injective
```

```
n + 1 <= m if n < m
```

```
Cauchy Schwarz
```

```
List.sum
```

```
algebraic elements x,y over K with same minimal polynomial
```

## Ресурсы

- [GitHub Repository](https://github.com/oOo0oOo/lean-lsp-mcp)

## Примечания

Внешние инструменты поиска ограничены до 3 запросов в 30 секунд. Требует ripgrep (rg) для функциональности локального поиска. Рекомендуется запустить 'lake build' вручную перед запуском MCP, чтобы избежать таймаутов. Совместим с Lean4 Theorem Proving Skill для Claude Desktop/Code.