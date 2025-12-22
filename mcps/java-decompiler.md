---
title: Java Decompiler MCP сервер
description: MCP сервер для декомпиляции Java class файлов в читаемый исходный код из путей к файлам, имен пакетов или JAR архивов с использованием декомпилятора CFR.
tags:
- Code
- DevOps
- Analytics
author: idachev
featured: false
install_command: claude mcp add javadc -s project -- npx -y @idachev/mcp-javadc
---

MCP сервер для декомпиляции Java class файлов в читаемый исходный код из путей к файлам, имен пакетов или JAR архивов с использованием декомпилятора CFR.

## Установка

### NPX (Рекомендуется)

```bash
npx -y @idachev/mcp-javadc
```

### Глобальная установка

```bash
npm install -g @idachev/mcp-javadc
mcpjavadc
```

### Из исходного кода

```bash
git clone https://github.com/idachev/mcp-javadc.git
cd mcp-javadc
npm install
npm start
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "mcpServers": {
    "javaDecompiler": {
      "command": "npx",
      "args": ["-y", "@idachev/mcp-javadc"],
      "env": {
        "CLASSPATH": "/path/to/java/classes"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `decompile-from-path` | Декомпилирует Java .class файл по пути к файлу |
| `decompile-from-package` | Декомпилирует Java класс по имени пакета (например, java.util.ArrayList) |
| `decompile-from-jar` | Декомпилирует Java класс из JAR файла с указанным именем класса |

## Возможности

- Декомпиляция Java .class файлов по пути к файлу
- Декомпиляция Java классов по имени пакета (например, java.util.ArrayList)
- Декомпиляция Java классов из JAR файлов
- Указание конкретного класса для извлечения из JAR файлов
- Полная совместимость с MCP API
- Stdio транспорт для бесшовной интеграции
- Корректная обработка ошибок
- Управление временными файлами

## Переменные окружения

### Опциональные
- `CLASSPATH` - Java classpath для поиска class файлов (используется когда classpath не указан)

## Ресурсы

- [GitHub Repository](https://github.com/idachev/mcp-javadc)

## Примечания

Не требует установки Java (использует JavaScript порт декомпилятора CFR). Можно тестировать интерактивно с помощью MCP Inspector: npx @modelcontextprotocol/inspector node ./index.js. Работает со стандартными Java class файлами, структурами пакетов, современными возможностями Java и JAR файлами. Для Maven репозиториев используйте команды find ~/.m2 для поиска JAR файлов и jar tf для просмотра доступных классов.