---
title: Druid MCP сервер
description: Комплексный сервер Model Context Protocol (MCP) для Apache Druid, который предоставляет обширные инструменты, ресурсы и промпты для управления и анализа кластеров Druid через AI ассистентов.
tags:
- Database
- Analytics
- Monitoring
- DevOps
- API
author: iunera
featured: false
---

Комплексный сервер Model Context Protocol (MCP) для Apache Druid, который предоставляет обширные инструменты, ресурсы и промпты для управления и анализа кластеров Druid через AI ассистентов.

## Установка

### Docker STDIO

```bash
docker run --rm -i \
  -e DRUID_ROUTER_URL=http://your-druid-router:8888 \
  -e DRUID_COORDINATOR_URL=http://your-druid-coordinator:8081 \
  iunera/druid-mcp-server:latest
```

### Docker HTTP

```bash
docker run -p 8080:8080 \
  -e SPRING_PROFILES_ACTIVE=http \
  -e DRUID_ROUTER_URL=http://your-druid-router:8888 \
  -e DRUID_COORDINATOR_URL=http://your-druid-coordinator:8081 \
  iunera/druid-mcp-server:latest
```

### Из исходных кодов

```bash
mvn clean package -DskipTests
java -jar target/druid-mcp-server-1.6.0.jar
```

### JAR из Maven Central

```bash
java -jar target/druid-mcp-server-1.6.0.jar
```

### JAR из Maven Central HTTP

```bash
java -Dspring.profiles.active=http \
     -jar target/druid-mcp-server-1.6.0.jar
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `listDatasources` | Список всех доступных имен источников данных Druid |
| `showDatasourceDetails` | Показать подробную информацию для конкретного источника данных, включая информацию о колонках |
| `killDatasource` | Окончательно удалить источник данных, убрав все данные и метаданные |
| `listLookups` | Список всех доступных Druid lookups от координатора |
| `getLookupConfig` | Получить конфигурацию для конкретного lookup |
| `updateLookupConfig` | Обновить конфигурацию для конкретного lookup |
| `listAllSegments` | Список всех сегментов по всем источникам данных |
| `getSegmentMetadata` | Получить метаданные для конкретных сегментов |
| `getSegmentsForDatasource` | Получить все сегменты для конкретного источника данных |
| `queryDruidSql` | Выполнить SQL запрос к источникам данных Druid |
| `viewRetentionRules` | Просмотреть правила удержания для всех источников данных или конкретного |
| `updateRetentionRules` | Обновить правила удержания для источника данных |
| `viewAllCompactionConfigs` | Просмотреть конфигурации компактирования для всех источников данных |
| `viewCompactionConfigForDatasource` | Просмотреть конфигурацию компактирования для конкретного источника данных |
| `editCompactionConfigForDatasource` | Редактировать конфигурацию компактирования для источника данных |

## Возможности

- Интеграция с Spring AI MCP сервером
- Архитектура на основе инструментов для соответствия протоколу MCP с автоматической генерацией JSON схем
- Множественные режимы транспорта: поддержка STDIO, SSE и Streamable HTTP, включая OAuth
- Коммуникация в реальном времени с Server-Sent Events и стриминговыми возможностями
- Настраиваемые шаблоны промптов с AI-управляемыми рекомендациями
- Комплексная обработка ошибок с корректными ответами
- Организация пакетов по функциям с автоматическим обнаружением
- Готовая для корпоративного использования production-grade конфигурация и функции безопасности
- Безопасность OAuth 2.0 для HTTP и SSE транспортов
- Комплексные инструменты управления кластером Druid

## Переменные окружения

### Обязательные
- `DRUID_ROUTER_URL` - URL сервиса роутера Druid
- `DRUID_COORDINATOR_URL` - URL сервиса координатора Druid

### Опциональные
- `SPRING_PROFILES_ACTIVE` - Профиль Spring для активации (установите 'http' для HTTP режима, по умолчанию STDIO)
- `DRUID_MCP_SECURITY_OAUTH2_ENABLED` - Включает или отключает безопасность OAuth2 для аутентификации клиентов

## Ресурсы

- [GitHub репозиторий](https://github.com/iunera/druid-mcp-server)

## Примечания

Требует Java 24 и Maven 3.6+. Сервер поддерживает режимы транспорта как STDIO, так и HTTP. OAuth 2.0 включен по умолчанию для HTTP и SSE транспортов. В режиме только для чтения инструменты, которые изменяют кластер Druid, не регистрируются. Интеграция с корпоративным SSO доступна через consulting@iunera.com. Разработано iunera - Решения для продвинутой AI и аналитики данных.