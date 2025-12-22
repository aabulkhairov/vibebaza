---
title: OpenLink Generic Java Database Connectivity MCP сервер
description: Легковесный Java-based MCP сервер для JDBC, который предоставляет возможности подключения к базе данных и выполнения запросов, совместимый с Virtuoso DBMS и любой DBMS с JDBC драйвером.
tags:
- Database
- Analytics
- Integration
- API
author: OpenLinkSoftware
featured: false
---

Легковесный Java-based MCP сервер для JDBC, который предоставляет возможности подключения к базе данных и выполнения запросов, совместимый с Virtuoso DBMS и любой DBMS с JDBC драйвером.

## Установка

### Из исходного кода

```bash
git clone https://github.com/OpenLinkSoftware/mcp-jdbc-server.git
cd mcp-jdbc-server
```

### MCP Inspector - Virtuoso

```bash
npm install -g @modelcontextprotocol/inspector
npx @modelcontextprotocol/inspector java -jar /path/to/mcp-jdbc-server/MCPServer-1.0.0-runner.jar
```

### MCP Inspector - Дополнительные драйверы

```bash
export CLASSPATH=$CLASSPATH:/path/to/driver1.jar:/path/to/driver2.jar:/path/to/driverN.jar
npx @modelcontextprotocol/inspector java -cp MCPServer-1.0.0-runner.jar:/path/to/driver1.jar:/path/to/driver2.jar:/path/to/driverN.jar io.quarkus.runner.GeneratedMain
```

## Конфигурация

### Claude Desktop - Virtuoso JDBC драйвер

```json
{
  "mcpServers": {
    "my_database": {
      "command": "java",
      "args": ["-jar", "/path/to/mcp-jdbc-server/MCPServer-1.0.0-runner.jar"],
      "env": {
        "jdbc.url": "jdbc:virtuoso://localhost:1111",
        "jdbc.user": "username",
        "jdbc.password": "password",
        "jdbc.api_key": "sk-xxx"
      }
    }
  }
}
```

### Claude Desktop - Другие JDBC драйверы

```json
"jdbc": {
  "command": "java",
  "args": [
    "-cp",
    "/path/to/mcp-jdbc-server/MCPServer-1.0.0-runner.jar:/path/to/jdbc_driver1.jar:/path/to/jdbc_driverN.jar",
    "io.quarkus.runner.GeneratedMain"
  ],
  "env": {
    "jdbc.url": "jdbc:virtuoso://localhost:1111",
    "jdbc.user": "dba",
    "jdbc.password": "dba"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `jdbc_get_schemas` | Получить список схем базы данных, доступных в подключенной системе управления базами данных (DBMS) |
| `jdbc_get_tables` | Получить список таблиц, связанных с выбранной схемой базы данных |
| `jdbc_describe_table` | Предоставить детальное описание таблицы, включая имена колонок, типы данных, обработку null-значений, автоинкремент... |
| `jdbc_filter_table_names` | Получить список таблиц на основе шаблона подстроки из выбранной схемы базы данных |
| `jdbc_query_database` | Выполнить SQL запрос и вернуть результаты в формате JSONL |
| `jdbc_execute_query` | Выполнить SQL запрос и вернуть результаты в формате JSONL |
| `jdbc_execute_query_md` | Выполнить SQL запрос и вернуть результаты в формате таблицы Markdown |
| `jdbc_spasql_query` | Выполнить SPASQL запрос и вернуть результаты (специфичная функция Virtuoso) |
| `jdbc_sparql_query` | Выполнить SPARQL запрос и вернуть результаты (специфичная функция Virtuoso) |
| `jdbc_virtuoso_support_ai` | Взаимодействовать с LLM через Virtuoso Support Assistant/агент (специфичная функция Virtuoso) |

## Возможности

- Получение схем: Извлечение и составление списка всех имен схем из подключенной базы данных
- Получение таблиц: Извлечение информации о таблицах для конкретных схем или всех схем
- Описание таблицы: Генерация детального описания структуры таблиц с именами колонок, типами данных, nullable атрибутами, первичными и внешними ключами
- Поиск таблиц: Фильтрация и извлечение таблиц на основе подстрок имен
- Выполнение хранимых процедур: Выполнение хранимых процедур и получение результатов (специфично для Virtuoso)
- Выполнение запросов: Поддержка формата результатов JSONL и формата таблицы Markdown
- Выполнение SPARQL и SPASQL запросов (специфично для Virtuoso)
- Интеграция с AI ассистентом через Virtuoso Support Assistant (специфично для Virtuoso)

## Переменные окружения

### Обязательные
- `jdbc.url` - Строка подключения JDBC URL
- `jdbc.user` - Имя пользователя базы данных
- `jdbc.password` - Пароль базы данных

### Опциональные
- `jdbc.api_key` - API ключ для функций AI сервиса

## Ресурсы

- [GitHub Repository](https://github.com/OpenLinkSoftware/mcp-jdbc-server)

## Примечания

Требует Java 21 или выше. Построен на фреймворке Quarkus. Поддерживает любую DBMS с JDBC драйвером. Включает специальные функции для Virtuoso DBMS, включая SPARQL/SPASQL запросы и интеграцию с AI ассистентом. Для дополнительных JDBC драйверов убедитесь, что JAR файлы зарегистрированы в JVM через $CLASSPATH.