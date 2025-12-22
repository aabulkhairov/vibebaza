---
title: Vibe Check MCP сервер
description: MCP сервер, который обеспечивает надзор за AI агентами через Chain-Pattern Interrupts (CPI), предотвращая переусложнение, расползание требований и несогласованность, выступая в роли мета-ментора, который ставит под сомнение предположения и удерживает агентов на пути минимально жизнеспособного решения.
tags:
- AI
- Monitoring
- Productivity
- Security
- Code
author: Community
featured: false
---

MCP сервер, который обеспечивает надзор за AI агентами через Chain-Pattern Interrupts (CPI), предотвращая переусложнение, расползание требований и несогласованность, выступая в роли мета-ментора, который ставит под сомнение предположения и удерживает агентов на пути минимально жизнеспособного решения.

## Установка

### NPX (STDIO)

```bash
npx -y @pv-bhat/vibe-check-mcp start --stdio
```

### NPX (HTTP)

```bash
npx -y @pv-bhat/vibe-check-mcp start --http --port 2091
```

### Из исходного кода

```bash
git clone https://github.com/PV-Bhat/vibe-check-mcp-server.git
cd vibe-check-mcp-server
npm ci
npm run build
npm test
```

### Docker

```bash
bash scripts/docker-setup.sh
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "vibe-check-mcp": {
      "command": "npx",
      "args": ["-y", "@pv-bhat/vibe-check-mcp", "start", "--stdio"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `vibe_check` | Ставит под сомнение предположения и предотвращает туннельное видение, предоставляя метакогнитивную обратную связь |
| `vibe_learn` | Фиксирует ошибки, предпочтения и успехи для будущего анализа |
| `update_constitution` | Устанавливает или объединяет наборы правил для конкретной сессии |
| `reset_constitution` | Очищает правила сессии для конкретной сессии |
| `check_constitution` | Возвращает действующие правила для конкретной сессии |

## Возможности

- Адаптивные прерывания CPI с подсказками, учитывающими фазу, которые ставят под сомнение предположения
- Поддержка множества провайдеров LLM (Gemini, OpenAI, Anthropic, OpenRouter)
- Непрерывность истории, которая обобщает предыдущие советы при предоставлении sessionId
- Конституция сессии для применения правил в рамках отдельных сессий
- Основанный на исследованиях надзор, улучшающий успех на +27% и снижающий вредные действия на -41%
- Самосовершенствование через логирование ошибок и распознавание паттернов

## Переменные окружения

### Опциональные
- `GEMINI_API_KEY` - API ключ для Gemini (провайдер по умолчанию)
- `OPENAI_API_KEY` - API ключ для OpenAI
- `OPENROUTER_API_KEY` - API ключ для OpenRouter
- `ANTHROPIC_API_KEY` - API ключ для Anthropic
- `ANTHROPIC_AUTH_TOKEN` - Bearer токен для Anthropic proxy
- `ANTHROPIC_BASE_URL` - Базовый URL для Anthropic API
- `ANTHROPIC_VERSION` - Версия API для Anthropic
- `DEFAULT_LLM_PROVIDER` - Провайдер LLM по умолчанию (gemini | openai | openrouter | anthropic)

## Примеры использования

```
Вызывайте vibe_check после планирования и перед важными действиями для получения метакогнитивной обратной связи
```

```
Используйте vibe_check для постановки под сомнение предположений и предотвращения переусложнения
```

```
Записывайте решенные проблемы с помощью vibe_learn для создания истории улучшений
```

```
Устанавливайте правила сессии с помощью инструментов конституции для применения ограничений типа 'никаких внешних сетевых вызовов' или 'предпочитать unit тесты перед рефакторингом'
```

## Ресурсы

- [GitHub Repository](https://github.com/PV-Bhat/vibe-check-mcp-server)

## Примечания

Этот сервер реализует методологию исследований Chain-Pattern Interrupts (CPI). Требует Node >=20. Представлен на PulseMCP как 'Самый популярный' и включен в официальный MCP репозиторий Anthropic. Поддерживает транспорты STDIO и HTTP. Имеет встроенные установщики клиентов для Claude Desktop, Cursor, Windsurf и VS Code.