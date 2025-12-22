---
title: Onyx MCP Sandbox MCP сервер
description: Безопасный MCP сервер для выполнения кода в изолированных Docker песочницах с поддержкой множества языков программирования, включая Python, Java, C, C++, JavaScript и Rust.
tags:
- Code
- Security
- DevOps
- Integration
- Productivity
author: avd1729
featured: false
---

Безопасный MCP сервер для выполнения кода в изолированных Docker песочницах с поддержкой множества языков программирования, включая Python, Java, C, C++, JavaScript и Rust.

## Установка

### Из исходников

```bash
go run ./cmd/server/main.go
```

### Сборка бинарника

```bash
go build -o sandbox_server ./cmd/server/main.go
```

### Загрузка Docker образов

```bash
docker pull python:3.11
docker pull openjdk:17
docker pull gcc:12
docker pull node:20
docker pull rust:1.72
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "onyx": {
      "command": "<absolute path>/sandbox_server.exe",
      "args": []
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `run_code` | Безопасно выполняет произвольный код в Docker песочницах с поддержкой множества языков программирования |

## Возможности

- Поддержка множества языков: Python, Java, C, C++, JavaScript/Node.js, Rust
- Docker песочницы с отключенной сетью и файловой системой только для чтения
- Ограничения по CPU, памяти и количеству процессов
- Выполнение без прав root для повышенной безопасности
- Подробное логирование в stderr для MCP клиентов
- Автоматические тесты через GitHub Actions
- Легкое расширение для новых языков программирования

## Ресурсы

- [GitHub Repository](https://github.com/avd1729/Onyx)

## Примечания

Требует Go 1.20+ и Docker Desktop/Engine. Рекомендуется предварительно загрузить Docker образы, чтобы избежать задержек при первом выполнении. Идеально подходит для продвинутых пользователей Claude Desktop или всех, кто создает AI рабочие процессы с выполняемым кодом.