---
title: OpenDigger MCP сервер
description: Model Context Protocol сервер для OpenDigger, который обеспечивает продвинутую аналитику репозиториев и инсайты через комплексные инструменты и промпты для анализа GitHub репозиториев.
tags:
- Analytics
- DevOps
- Code
- API
- Productivity
author: X-lab2017
featured: false
---

Model Context Protocol сервер для OpenDigger, который обеспечивает продвинутую аналитику репозиториев и инсайты через комплексные инструменты и промпты для анализа GitHub репозиториев.

## Установка

### Из исходного кода

```bash
git clone https://github.com/X-lab2017/open-digger-mcp-server.git
cd open-digger-mcp-server && cd mcp-server
npm install
npm run build
npm start
```

## Конфигурация

### Cursor MCP

```json
{
  "mcpServers": {
    "open-digger": {
      "command": "node",
      "args": ["/full/path/to/dist/index.js"],
      "cwd": "/full/path/to/project",
      "env": {
        "CACHE_TTL_SECONDS": "300"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_open_digger_metric` | Получение метрик одного репозитория |
| `get_open_digger_metrics_batch` | Пакетные операции для множественных метрик |
| `compare_repositories` | Сравнительный анализ нескольких репозиториев |
| `analyze_trends` | Анализ трендов роста за временные периоды |
| `get_ecosystem_insights` | Аналитика и инсайты экосистемы |
| `server_health` | Системная диагностика и мониторинг здоровья (Beta) |

## Возможности

- 6 комплексных инструментов для аналитики репозиториев
- 3 специализированных промпта для разных типов анализа
- Поддержка 20+ метрик включая openrank, stars, forks, contributors, bus_factor
- Сравнение репозиториев и конкурентный анализ
- Анализ трендов роста за временные периоды
- Комплексные отчеты о здоровье репозиториев
- Анализ активности и вклада разработчиков
- Аналитика и инсайты экосистемы
- Пакетные операции для множественных метрик
- Поддержка кэширования для улучшения производительности

## Переменные окружения

### Опциональные
- `CACHE_TTL_SECONDS` - Время жизни конфигурации кэша в секундах
- `SSE_PORT` - Опциональный порт SSE сервера
- `SSE_HOST` - Опциональный хост SSE сервера

## Примеры использования

```
Сравните microsoft/vscode и facebook/react используя инструмент compare_repositories
```

```
Сгенерируйте отчет о здоровье для microsoft/vscode используя промпт repo_health_analysis
```

```
Проанализируйте тренды роста для contributors в microsoft/vscode за 2 года
```

## Ресурсы

- [GitHub Repository](https://github.com/X-lab2017/open-digger-mcp-server)

## Примечания

Сервер предоставляет 3 специализированных промпта: repo_health_analysis (комплексные отчеты о здоровье репозиториев), repo_comparison (конкурентный анализ репозиториев) и developer_insights (анализ активности разработчиков). Поддерживает обширные метрики включая основные метрики (openrank, stars, forks, contributors), расширенные метрики (technical_fork, bus_factor, releases) и дополнительные метрики (change_requests, issue_response_time, code_change_lines). Совместим с Cursor AI IDE, VS Code, Claude Chat и MCP Inspector.