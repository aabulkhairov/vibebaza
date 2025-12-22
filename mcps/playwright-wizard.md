---
title: Playwright Wizard MCP сервер
description: Интеллектуальный сервер Model Context Protocol (MCP), который проведёт вас через создание профессиональных тестовых наборов Playwright с встроенными лучшими практиками, используя пошаговый мастер-процесс.
tags:
- Code
- DevOps
- Browser
- Productivity
author: Community
featured: false
---

Интеллектуальный сервер Model Context Protocol (MCP), который проведёт вас через создание профессиональных тестовых наборов Playwright с встроенными лучшими практиками, используя пошаговый мастер-процесс.

## Установка

### NPX (Рекомендуется)

```bash
npx -y playwright-wizard-mcp
```

### Глобальная установка

```bash
npm install -g playwright-wizard-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "playwright-wizard": {
      "command": "npx",
      "args": ["-y", "playwright-wizard-mcp"]
    }
  }
}
```

### GitHub Copilot (VS Code)

```json
{
  "servers": {
    "playwright-wizard": {
      "command": "npx",
      "args": ["-y", "playwright-wizard-mcp@latest"],
      "type": "stdio"
    }
  }
}
```

### Cline (VS Code)

```json
{
  "mcpServers": {
    "playwright-wizard": {
      "command": "npx",
      "args": ["-y", "playwright-wizard-mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `analyze-app` | Анализирует структуру вашего приложения и технологический стек |
| `generate-test-plan` | Создаёт комплексные тестовые сценарии и критерии приёмки |
| `setup-infrastructure` | Настраивает конфиг Playwright, фикстуры и структуру папок |
| `generate-page-objects` | Генерирует типобезопасные модели объектов страниц с оптимальными селекторами |
| `implement-test-suite` | Пишет актуальные тесты с проверками и обработкой ошибок |
| `setup-ci-cd` | Добавляет GitHub Actions для автоматизированного тестирования |
| `add-accessibility` | Интегрирует axe-core для соответствия WCAG 2.1 AA |
| `add-api-testing` | Добавляет тестирование REST/GraphQL/tRPC API |
| `advanced-optimization` | Глубокая оптимизация производительности и переиспользование состояний авторизации |
| `reference-core-principles` | Основные принципы тестирования и стандарты качества |
| `reference-workflow-overview` | Полное объяснение процесса работы и связей между промптами |
| `reference-mcp-setup` | Настройка MCP сервера и паттерны использования |
| `reference-selector-strategies` | Лучшие практики селекторов и оценка качества HTML |
| `reference-fixture-patterns` | Паттерны фикстур Playwright для параллельного выполнения |
| `reference-data-storage-patterns` | Паттерны хранения тестовых данных (ORM, JSON, MSW) |

## Возможности

- Пошаговый мастер-процесс для создания комплексных тестовых наборов
- Исчерпывающие промпты, покрывающие анализ, планирование, настройку и реализацию
- Лучшие практики для селекторов, фикстур и параллельного выполнения
- Опциональные улучшения для тестирования доступности и API
- Справочная документация по продвинутым паттернам
- Интеграция с MCP Registry для лёгкого поиска и установки
- Генерация типобезопасных моделей объектов страниц
- Автоматическое обнаружение и анализ технологического стека
- Интеграция с CI/CD через GitHub Actions
- Интеграция тестирования доступности через axe-core

## Примеры использования

```
Используй инструмент analyze-app, чтобы помочь мне понять моё приложение
```

```
Запусти инструмент generate-test-plan для создания тестовых сценариев
```

```
Используй setup-infrastructure для настройки Playwright
```

```
Помоги мне проанализировать моё React приложение для тестирования с Playwright
```

```
Создай план тестирования на основе анализа
```

## Ресурсы

- [GitHub Repository](https://github.com/oguzc/playwright-wizard-mcp)

## Примечания

Мастер создаёт документацию процесса работы в папке `.playwright-wizard-mcp/` в корне вашего проекта для отслеживания прогресса. Поддерживает React, TypeScript, Vite и другие современные веб-технологии. Доступен в официальном MCP Registry для лёгкого поиска.