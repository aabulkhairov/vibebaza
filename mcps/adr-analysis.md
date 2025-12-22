---
title: ADR Analysis MCP сервер
description: AI-сервер для анализа Architectural Decision Records (ADR). Предоставляет
  архитектурные инсайты, детекцию технологического стека, проверки безопасности и улучшение
  TDD workflow для проектов разработки.
tags:
- AI
- Code
- Security
- Analytics
- DevOps
author: tosin2013
featured: false
---

AI-сервер для анализа Architectural Decision Records (ADR). Предоставляет архитектурные инсайты, детекцию технологического стека, проверки безопасности и улучшение TDD workflow для проектов разработки.

## Установка

### NPM Global

```bash
npm install -g mcp-adr-analysis-server
```

### NPX

```bash
npx mcp-adr-analysis-server
```

### RHEL 9/10 установщик

```bash
curl -sSL https://raw.githubusercontent.com/tosin2013/mcp-adr-analysis-server/main/scripts/install-rhel.sh | bash
```

### Из исходников

```bash
git clone https://github.com/tosin2013/mcp-adr-analysis-server.git
cd mcp-adr-analysis-server
npm install && npm run build && npm test
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "adr-analysis": {
      "command": "mcp-adr-analysis-server",
      "env": {
        "PROJECT_PATH": "/path/to/your/project",
        "OPENROUTER_API_KEY": "your_key_here",
        "EXECUTION_MODE": "full"
      }
    }
  }
}
```

## Возможности

- AI-инсайты архитектуры с интеграцией OpenRouter.ai
- Детекция технологий и идентификация архитектурных паттернов
- Генерация, предложение и поддержка ADR
- Умная линковка кода с AI-поиском
- Безопасность и compliance с автоматическим маскированием контента
- Интеграция с Test-Driven Development с двухфазной валидацией
- Валидация готовности к деплою с zero-tolerance тестированием
- Tree-sitter AST анализ
- Веб-ресёрч через интеграцию с Firecrawl
- 95% confidence scoring для результатов анализа

## Переменные окружения

### Обязательные
- `OPENROUTER_API_KEY` — API ключ для интеграции с OpenRouter.ai
- `PROJECT_PATH` — путь к директории проекта для анализа
- `EXECUTION_MODE` — установить в 'full' для включения полных возможностей анализа

### Опциональные
- `FIRECRAWL_ENABLED` — включить веб-ресёрч через Firecrawl
- `FIRECRAWL_API_KEY` — API ключ для облачного сервиса Firecrawl
- `FIRECRAWL_BASE_URL` — базовый URL для self-hosted инстанса Firecrawl

## Примеры использования

```
Analyze this React project's architecture and suggest ADRs for any implicit decisions
```

```
Generate ADRs from the PRD.md file and create a todo.md with implementation tasks
```

```
Check this codebase for security issues and provide masking recommendations
```

## Ресурсы

- [GitHub Repository](https://github.com/tosin2013/mcp-adr-analysis-server)

## Примечания

Возвращает реальные результаты анализа, а не промпты для отправки куда-то ещё. Поддерживает несколько AI-ассистентов: Claude, Cline, Cursor, Windsurf. Требуется Node.js 20+ и TypeScript 5.9+. Включает >80% тестовое покрытие и комплексные функции безопасности.
