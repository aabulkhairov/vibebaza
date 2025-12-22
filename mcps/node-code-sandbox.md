---
title: Node Code Sandbox MCP сервер
description: Node.js MCP сервер, который выполняет JavaScript код в изолированных Docker контейнерах с автоматической установкой npm зависимостей и возможностью вывода файлов.
tags:
- Code
- DevOps
- Docker
- Security
- Integration
author: alfonsograziano
featured: true
---

Node.js MCP сервер, который выполняет JavaScript код в изолированных Docker контейнерах с автоматической установкой npm зависимостей и возможностью вывода файлов.

## Установка

### NPX

```bash
npx -y node-code-sandbox-mcp
```

### Docker

```bash
docker run --rm -it \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v "$HOME/Desktop/sandbox-output":"/root" \
  -e FILES_DIR="$HOME/Desktop/sandbox-output" \
  -e SANDBOX_MEMORY_LIMIT="512m" \
  -e SANDBOX_CPU_LIMIT="0.5" \
  mcp/node-code-sandbox stdio
```

### Из исходников

```bash
npm install
npm run build
```

## Конфигурация

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "js-sandbox": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-v",
        "/var/run/docker.sock:/var/run/docker.sock",
        "-v",
        "$HOME/Desktop/sandbox-output:/root",
        "-e",
        "FILES_DIR=$HOME/Desktop/sandbox-output",
        "-e",
        "SANDBOX_MEMORY_LIMIT=512m",
        "-e",
        "SANDBOX_CPU_LIMIT=0.75",
        "mcp/node-code-sandbox"
      ]
    }
  }
}
```

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "node-code-sandbox-mcp": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "node-code-sandbox-mcp"],
      "env": {
        "FILES_DIR": "/Users/alfonsograziano/Desktop/node-sandbox",
        "SANDBOX_MEMORY_LIMIT": "512m",
        "SANDBOX_CPU_LIMIT": "0.75"
      }
    }
  }
}
```

### VS Code

```json
"mcp": {
    "servers": {
        "js-sandbox": {
            "command": "docker",
            "args": [
                "run",
                "-i",
                "--rm",
                "-v", "/var/run/docker.sock:/var/run/docker.sock",
                "-v", "$HOME/Desktop/sandbox-output:/root",
                "-e", "FILES_DIR=$HOME/Desktop/sandbox-output",
                "-e", "SANDBOX_MEMORY_LIMIT=512m",
                "-e", "SANDBOX_CPU_LIMIT=1",
                "mcp/node-code-sandbox"
              ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `run_js_ephemeral` | Запускает одноразовый JavaScript скрипт в новом временном контейнере с автоматическим сохранением выходных файлов |
| `sandbox_initialize` | Создает новый контейнер песочницы для сеансовых исполнений |
| `sandbox_exec` | Выполняет shell команды внутри работающего контейнера песочницы |
| `run_js` | Устанавливает npm зависимости и выполняет JavaScript код в существующей песочнице с опциональным отсоединением... |
| `sandbox_stop` | Останавливает и удаляет контейнер песочницы |
| `search_npm_packages` | Ищет npm пакеты по ключевому слову и получает их название, описание и фрагмент README |

## Возможности

- Запуск и управление изолированными Node.js контейнерами песочницы
- Выполнение произвольных shell команд внутри контейнеров
- Установка указанных npm зависимостей для каждой задачи
- Запуск ES модулей JavaScript и захват stdout
- Корректное завершение работы контейнеров
- Режим отсоединения: сохранение контейнеров после выполнения скриптов для долго работающих серверов
- Автоматическое сохранение выходных файлов (изображения и текстовые файлы)
- Контролируемые лимиты CPU/памяти для контейнеров
- Функция поиска npm пакетов

## Переменные окружения

### Опциональные
- `FILES_DIR` - Путь к директории для постоянного сохранения выходных файлов из контейнеров песочницы
- `SANDBOX_MEMORY_LIMIT` - Лимит памяти для контейнеров песочницы (например, '512m')
- `SANDBOX_CPU_LIMIT` - Лимит CPU для контейнеров песочницы (например, '0.75')

## Примеры использования

```
Создать и запустить JS скрипт с console.log("Hello World")
```

```
Создать и запустить JS скрипт, который генерирует QR код для URL `https://nodejs.org/en`, и сохранить его как `qrcode.png` **Совет:** Используйте пакет `qrcode`.
```

## Ресурсы

- [GitHub Repository](https://github.com/alfonsograziano/node-code-sandbox-mcp)

## Примечания

Требует установленный и запущенный Docker. Предварительно загрузите Docker образы (node:lts-slim, mcr.microsoft.com/playwright:v1.55.0-noble, alfonsograziano/node-chartjs-canvas:latest) чтобы избежать задержек при первом выполнении. Доступен в Docker Hub как mcp/node-code-sandbox. Сеансовые инструменты идеальны для долгоживущих контейнеров, одноразовое выполнение отлично подходит для быстрых экспериментов.