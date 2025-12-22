---
title: Maven Tools MCP сервер
description: MCP сервер, предоставляющий AI-помощникам информацию о зависимостях Maven Central для всех JVM инструментов сборки (Maven, Gradle, SBT, Mill). Читает maven-metadata.xml файлы напрямую из Maven Central для мгновенного получения точной информации о зависимостях с интеграцией Context7 для поддержки документации.
tags:
- DevOps
- Code
- Analytics
- Integration
- API
author: arvindand
featured: false
---

MCP сервер, предоставляющий AI-помощникам информацию о зависимостях Maven Central для всех JVM инструментов сборки (Maven, Gradle, SBT, Mill). Читает maven-metadata.xml файлы напрямую из Maven Central для мгновенного получения точной информации о зависимостях с интеграцией Context7 для поддержки документации.

## Установка

### Docker

```bash
docker run -i --rm arvindand/maven-tools-mcp:latest
```

### Docker (без Context7)

```bash
docker run -i --rm arvindand/maven-tools-mcp:latest-noc7
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "maven-tools": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm",
        "arvindand/maven-tools-mcp:latest"
      ]
    }
  }
}
```

### VS Code Workspace

```json
{
  "servers": {
    "maven-tools": {
      "type": "stdio",
      "command": "docker",
      "args": ["run", "-i", "--rm", "arvindand/maven-tools-mcp:latest"]
    }
  }
}
```

### VS Code User Settings

```json
{
  "mcp": {
    "servers": {
      "maven-tools": {
        "type": "stdio", 
        "command": "docker",
        "args": ["run", "-i", "--rm", "arvindand/maven-tools-mcp:latest"]
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_latest_version` | Получить новейшую версию по типу с настройками стабильности |
| `check_version_exists` | Проверить существование конкретной версии с информацией о типе |
| `check_multiple_dependencies` | Проверить несколько зависимостей с фильтрацией и массовыми операциями |
| `compare_dependency_versions` | Сравнить текущую и последнюю версии с рекомендациями по обновлению |
| `analyze_dependency_age` | Классифицировать зависимости как свежие/текущие/устаревающие/устаревшие |
| `analyze_release_patterns` | Анализировать активность поддержки и прогнозировать релизы |
| `get_version_timeline` | Расширенная временная линия версий с темпоральным анализом |
| `analyze_project_health` | Комплексный анализ состояния для множественных зависимостей |
| `resolve-library-id` | Поиск документации библиотеки с использованием Context7 |
| `get-library-docs` | Получить документацию библиотеки по Context7 ID |

## Возможности

- Универсальная поддержка всех JVM инструментов сборки (Maven, Gradle, SBT, Mill)
- Массовые операции - анализ 20+ зависимостей за один вызов
- Сравнение версий с анализом влияния обновления (major/minor/patch)
- Фильтрация стабильности - только стабильные версии или включая пре-релизы
- Корпоративная производительность с кэшированными ответами <100мс
- Анализ возраста зависимостей и классификация свежести
- Анализ паттернов релизов и оценка активности поддержки
- Интеграция Context7 для поддержки документации
- Поддержка мультиархитектурного Docker (AMD64/ARM64)
- Оценка рисков критических изменений перед обновлением

## Примеры использования

```
Check all dependencies in this build file for latest versions
```

```
What's the latest Spring Boot version?
```

```
Which dependencies in my project need updates?
```

```
Show me only stable versions for production deployment
```

```
How old are my dependencies and which ones need attention?
```

## Ресурсы

- [GitHub Repository](https://github.com/arvindand/maven-tools-mcp)

## Примечания

Интеграция Context7 включена по умолчанию и обращается к https://mcp.context7.com во время запуска. Используйте образ без Context7 (latest-noc7), если ваша сеть блокирует этот URL. Корпоративные сети с SSL-инспекцией могут создавать пользовательские образы с корпоративными сертификатами, используя руководство по корпоративным сертификатам.