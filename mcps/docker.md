---
title: Docker MCP сервер
description: Комплексный Model Context Protocol (MCP) сервер, который предоставляет расширенные Docker операции через унифицированный интерфейс, объединяя 16 мощных Docker MCP инструментов с 25+ удобными CLI алиасами для полного управления Docker рабочими процессами.
tags:
- DevOps
- Code
- Productivity
- Integration
- Cloud
author: 0xshariq
featured: false
---

Комплексный Model Context Protocol (MCP) сервер, который предоставляет расширенные Docker операции через унифицированный интерфейс, объединяя 16 мощных Docker MCP инструментов с 25+ удобными CLI алиасами для полного управления Docker рабочими процессами.

## Установка

### NPM Global

```bash
npm install -g @0xshariq/docker-mcp-server
```

### PNPM Global

```bash
pnpm add -g @0xshariq/docker-mcp-server
```

### Из исходников

```bash
git clone https://github.com/0xshariq/docker-mcp-server.git
cd docker-mcp-server
npm install
npm run build
npm link
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "docker": {
      "command": "node",
      "args": ["/path/to/docker-mcp-server/dist/index.js"]
    }
  }
}
```

## Возможности

- 16 мощных Docker MCP инструментов с 25+ CLI алиасами
- Полное управление жизненным циклом контейнеров от сборки до публикации
- Интеграция с мульти-контейнерным Docker Compose с оркестрацией сервисов
- Безопасные операции с реестрами для Docker Hub, AWS ECR, Azure ACR, Google GCR
- Расширенное управление сетями и томами
- Интеллектуальная очистка системы с несколькими уровнями безопасности
- Кроссплатформенная поддержка для Linux, macOS и Windows
- Дизайн с приоритетом безопасности с операциями паролей, управляемыми Docker
- Нулевое раскрытие паролей в истории команд или списках процессов
- Поддержка аутентификации по токенам для CI/CD пайплайнов

## Примеры использования

```
List all running containers
```

```
List Docker images
```

```
Run an interactive Ubuntu container
```

```
Start Docker Compose services
```

```
Login to Docker registries
```

## Ресурсы

- [GitHub Repository](https://github.com/0xshariq/docker-mcp-server)

## Примечания

Требует Node.js 18+ и установленный Docker. Сервер предоставляет как интеграцию с протоколом MCP для совместимых инструментов, так и автономные CLI команды. Доступен универсальный скрипт запуска для автоматической настройки с любым MCP клиентом. Совместим с Claude Desktop, Cursor IDE, Continue (VS Code), Open WebUI и другими.