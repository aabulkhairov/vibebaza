---
title: Octocode MCP сервер
description: Сервер Model Context Protocol, который позволяет AI-ассистентам искать, анализировать и извлекать полезную информацию из миллионов GitHub репозиториев с корпоративным уровнем безопасности и эффективным использованием токенов.
tags:
- Code
- Search
- AI
- Analytics
- API
author: bgauryy
featured: true
install_command: claude mcp add octocode npx octocode-mcp@latest
---

Сервер Model Context Protocol, который позволяет AI-ассистентам искать, анализировать и извлекать полезную информацию из миллионов GitHub репозиториев с корпоративным уровнем безопасности и эффективным использованием токенов.

## Установка

### NPX

```bash
npx octocode-mcp@latest
```

## Конфигурация

### Стандартная конфигурация

```json
{
  "mcpServers": {
    "octocode": {
      "command": "npx",
      "args": [
        "octocode-mcp@latest"
      ]
    }
  }
}
```

### Amp

```json
"amp.mcpServers": {
  "octocode": {
    "command": "npx",
    "args": [
      "octocode-mcp@latest"
    ]
  }
}
```

### Cursor для конкретного проекта

```json
{
  "mcpServers": {
    "octocode": {
      "command": "npx",
      "args": ["octocode-mcp@latest"]
    }
  }
}
```

### Cline

```json
{
  "mcpServers": {
    "octocode": {
      "command": "npx",
      "args": [
        "octocode-mcp@latest"
      ]
    }
  }
}
```

## Возможности

- Поиск и анализ миллионов GitHub репозиториев
- Корпоративный уровень безопасности с эффективным использованием токенов
- Умная оркестрация инструментов для исследований
- Интеллектуальное принятие решений на всем протяжении исследовательского процесса
- Многоцелевые исследования для обнаружения функций, понимания кода, расследования багов
- Специализированные воркфлоу для технических исследований, продуктовых исследований, анализа паттернов
- Прозрачное обоснование с показом использования инструментов и стратегии поиска
- Адаптивная стратегия для публичных репозиториев, приватных организаций и конкретных репозиториев
- Кросс-валидация результатов с использованием множества инструментов
- Практичные инсайты с готовыми к реализации планами

## Примеры использования

```
Use Octocode MCP for Deep Research - I want to build an application with chat (front-end) that shows a chat window to the user. The user enters a prompt in the chat, and the application sends the prompt to an Express backend that uses AI to process the request.
```

```
/octocode/research How can I use LangChain, LangGraph, and similar open-source AI tools to create agentic flows between agents for goal-oriented tasks? Can you suggest UI frameworks I can use to build a full-stack AI application?
```

```
list top repositories for: Stock market APIs (Typescript), Cursor rules examples, UI for AI, Mobile development using React, State management for React
```

```
How React implemented useState under the hood?
```

## Ресурсы

- [GitHub Repository](https://github.com/bgauryy/octocode-mcp)

## Примечания

Требует Node.js >= 18.12.0 и аутентификацию GitHub (либо GitHub CLI, либо Personal Access Token с правами repo, read:user, read:org). Сервер поддерживает множество клиентов, включая VS Code, Cursor, Claude Desktop, Amp, Codex, Cline, Gemini CLI, Goose, Kiro, LM Studio, opencode и Qodo Gen.