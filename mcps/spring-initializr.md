---
title: Spring Initializr MCP сервер
description: MCP сервер, который предоставляет доступ к функциональности Spring Initializr,
  позволяя AI-ассистентам программно генерировать и скачивать проекты Spring Boot
  с пользовательскими конфигурациями.
tags:
- Code
- DevOps
- Productivity
author: Community
featured: false
---

MCP сервер, который предоставляет доступ к функциональности Spring Initializr, позволяя AI-ассистентам программно генерировать и скачивать проекты Spring Boot с пользовательскими конфигурациями.

## Установка

### Готовые бинарники

```bash
Download the appropriate binary for your platform from the Releases page:
- Linux x64: springinitializr-mcp-linux-x64
- Windows x64: springinitializr-mcp-windows-x64.exe
- macOS x64: springinitializr-mcp-macos-x64
- macOS ARM64: springinitializr-mcp-macos-arm64
```

### Из исходного кода

```bash
git clone https://github.com/hpalma/springinitializr-mcp.git
cd springinitializr-mcp
./gradlew build
./gradlew nativeCompile
```

## Конфигурация

### Claude Desktop (macOS/Linux)

```json
{
  "mcpServers": {
    "springinitializr": {
      "command": "/path/to/springinitializr-mcp-binary"
    }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "springinitializr": {
      "command": "C:\\path\\to\\springinitializr-mcp-windows-x64.exe"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate-spring-boot-project` | Генерирует и скачивает проект Spring Boot с указанной конфигурацией |

## Возможности

- Генерация проектов Spring Boot с пользовательскими конфигурациями
- Поддержка различных типов проектов (Maven/Gradle), языков (Java/Kotlin/Groovy) и версий Java
- Автоматическое добавление популярных зависимостей Spring Boot
- Нативная компиляция с GraalVM для быстрого запуска
- Кросс-платформенные нативные бинарники для Linux, Windows и macOS
- Автоматическое извлечение скачанных ZIP-файлов
- Динамическое получение метаданных последних версий Spring Boot и зависимостей

## Примеры использования

```
Create a Spring Boot web application with Spring Data JPA, PostgreSQL, and Spring Security dependencies
```

```
Generate a Kotlin Spring Boot project using Gradle with WebFlux and MongoDB
```

```
Create a Maven-based Spring Boot project with Thymeleaf, Validation, and Actuator
```

## Ресурсы

- [GitHub Repository](https://github.com/hpalma/springinitializr-mcp)

## Примечания

Сервер поддерживает все зависимости Spring Initializr, включая Web, Security, Data, Messaging, Cloud, Ops, AI и Testing фреймворки. Список зависимостей автоматически обновляется путем получения последних метаданных из Spring Initializr. Для сборки из исходного кода требуется Java 24 и GraalVM.