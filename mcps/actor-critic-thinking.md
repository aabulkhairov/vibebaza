---
title: Actor Critic Thinking MCP сервер
description: Сервер для двухперспективного анализа мышления. Обеспечивает комплексную
  оценку производительности через методологию Actor-Critic, чередуя перспективы создателя/исполнителя
  и аналитика/оценщика.
tags:
- AI
- Analytics
- Productivity
author: aquarius-wing
featured: false
---

Сервер для двухперспективного анализа мышления. Обеспечивает комплексную оценку производительности через методологию Actor-Critic, чередуя перспективы создателя/исполнителя и аналитика/оценщика.

## Установка

### NPX

```bash
npx -y mcp-server-actor-critic-thinking
```

### Из исходников

```bash
npm run build
node dist/index.js
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "actor-critic-thinking": {
      "command": "npx",
      "args": ["-y", "mcp-server-actor-critic-thinking"]
    }
  }
}
```

## Возможности

- Двухперспективный анализ: чередование между actor (создатель/исполнитель) и critic (аналитик/оценщик)
- Отслеживание раундов двухперспективного анализа
- Сбалансированная оценка: сочетание эмпатического понимания с объективным анализом
- Многомерная оценка: генерация нюансированных, многомерных оценок
- Действенная обратная связь: конструктивные предложения по улучшению

## Примеры использования

```
Generate creative, memorable, and marketable product names based on the provided description and keywords for a noise-canceling, wireless, over-ear headphone with a 20-hour battery life and touch controls
```

## Ресурсы

- [GitHub Repository](https://github.com/aquarius-wing/actor-critic-thinking-mcp)

## Примечания

Сервер требует специфических параметров: content, role (actor/critic), nextRoundNeeded boolean, thoughtNumber и totalThoughts. Сценарии использования включают оценку художественных перформансов, творческих работ, стратегических решений, performance reviews и сложных сценариев, требующих как эмпатии, так и объективности.
