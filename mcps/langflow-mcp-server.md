---
title: Langflow MCP Server MCP сервер
description: Комплексный MCP сервер, который предоставляет AI-ассистентам доступ к платформе автоматизации рабочих процессов Langflow, позволяя управлять потоками, выполнять рабочие процессы, операции сборки и взаимодействовать с базами знаний.
tags:
- AI
- Integration
- API
- Productivity
- Analytics
author: nobrainer-tech
featured: false
---

Комплексный MCP сервер, который предоставляет AI-ассистентам доступ к платформе автоматизации рабочих процессов Langflow, позволяя управлять потоками, выполнять рабочие процессы, операции сборки и взаимодействовать с базами знаний.

## Установка

### NPM Global

```bash
npm install -g langflow-mcp-server
```

### Из исходников

```bash
git clone https://github.com/nobrainer-tech/langflow-mcp.git
cd langflow-mcp
npm install
npm run build
cp .env.example .env
```

### Docker Compose

```bash
git clone https://github.com/nobrainer-tech/langflow-mcp.git
cd langflow-mcp
cp .env.example .env
docker-compose up -d
```

### Docker Build

```bash
docker build -t langflow-mcp-server:latest .
docker run -it --rm -e LANGFLOW_BASE_URL=http://localhost:7860 -e LANGFLOW_API_KEY=your-api-key langflow-mcp-server:latest
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "langflow": {
      "command": "npx",
      "args": ["-y", "langflow-mcp-server"],
      "env": {
        "LANGFLOW_BASE_URL": "http://localhost:7860",
        "LANGFLOW_API_KEY": "your-api-key-here",
        "MCP_MODE": "stdio",
        "LOG_LEVEL": "error"
      }
    }
  }
}
```

### Claude Desktop (локально)

```json
{
  "mcpServers": {
    "langflow": {
      "command": "node",
      "args": ["/absolute/path/to/langflow-mcp/dist/mcp/index.js"],
      "env": {
        "LANGFLOW_BASE_URL": "http://localhost:7860",
        "LANGFLOW_API_KEY": "your-api-key-here",
        "MCP_MODE": "stdio",
        "LOG_LEVEL": "error"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `create_flow` | Создать новый поток Langflow |
| `list_flows` | Список всех потоков с пагинацией и фильтрацией |
| `get_flow` | Получить детали конкретного потока по ID |
| `update_flow` | Обновить существующий поток |
| `delete_flow` | Удалить отдельный поток |
| `delete_flows` | Удалить несколько потоков одновременно |
| `run_flow` | Выполнить поток с конфигурацией входных данных (поддерживает стриминг) |
| `trigger_webhook` | Запустить поток через webhook |
| `build_flow` | Собрать/скомпилировать поток и получить job_id для асинхронного выполнения |
| `get_build_status` | Проверить статус сборки и события для конкретной задачи |
| `cancel_build` | Отменить выполняющуюся задачу сборки |
| `upload_flow` | Загрузить поток из JSON данных |
| `download_flows` | Скачать несколько потоков как JSON экспорт |
| `get_basic_examples` | Получить предварительно созданные примеры потоков |
| `list_folders` | Список всех папок с пагинацией |

## Возможности

- 90 инструментов для комплексного управления Langflow (94 с устаревшими инструментами)
- Управление потоками - создание, чтение, обновление, удаление и выполнение потоков
- Выполнение потоков - запуск потоков с входными данными и триггеры webhooks
- Операции сборки - компиляция, валидация и мониторинг сборок потоков
- Импорт/экспорт - загрузка и скачивание потоков и проектов
- Организация - управление папками и проектами
- Конфигурация - управление глобальными переменными
- Базы знаний - управление коллекциями документов RAG
- Обнаружение компонентов - список всех доступных компонентов Langflow
- Поддержка Docker деплоя с HTTP и STDIO режимами

## Переменные окружения

### Обязательные
- `LANGFLOW_BASE_URL` - URL инстанса Langflow
- `LANGFLOW_API_KEY` - API ключ для аутентификации в Langflow

### Опциональные
- `MCP_MODE` - Режим для MCP сервера (stdio или http)
- `LOG_LEVEL` - Уровень логирования (info, error, debug)
- `ENABLE_DEPRECATED_TOOLS` - Включить/отключить устаревшие инструменты (по умолчанию: true)
- `PORT` - Порт для HTTP режима
- `AUTH_TOKEN` - Токен аутентификации для HTTP режима

## Примеры использования

```
Создать новый поток автоматизации для обработки данных
```

```
Показать все мои существующие потоки с пагинацией
```

```
Выполнить конкретный поток с пользовательскими входными данными
```

```
Собрать и проверить поток на наличие ошибок
```

```
Загрузить новый поток из JSON конфигурации
```

## Ресурсы

- [GitHub Repository](https://github.com/nobrainer-tech/langflow-mcp)

## Примечания

Сервер включает 4 устаревших инструмента, соответствующих устаревшим endpoints в Langflow API 1.6.4. Они включены по умолчанию, но могут быть отключены с помощью ENABLE_DEPRECATED_TOOLS=false. Сервер поддерживает как Docker деплой, так и прямую npm установку, с комплексным покрытием API для автоматизации рабочих процессов Langflow.