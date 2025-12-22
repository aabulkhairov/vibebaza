---
title: DesktopCommander MCP сервер
description: Комплексный MCP сервер, который позволяет ИИ выполнять команды терминала,
  управлять файлами и директориями, запускать процессы в интерактивном режиме и автоматизировать
  задачи разработки на вашем локальном компьютере.
tags:
- Code
- DevOps
- Productivity
- Integration
- Analytics
author: wonderwhy-er
featured: true
---

Комплексный MCP сервер, который позволяет ИИ выполнять команды терминала, управлять файлами и директориями, запускать процессы в интерактивном режиме и автоматизировать задачи разработки на вашем локальном компьютере.

## Установка

### NPX Настройка

```bash
npx @wonderwhy-er/desktop-commander@latest setup
```

### NPX Режим отладки

```bash
npx @wonderwhy-er/desktop-commander@latest setup --debug
```

### Bash установщик (macOS)

```bash
curl -fsSL https://raw.githubusercontent.com/wonderwhy-er/DesktopCommanderMCP/refs/heads/main/install.sh | bash
```

### Из исходного кода

```bash
git clone https://github.com/wonderwhy-er/DesktopCommanderMCP.git
cd DesktopCommanderMCP
npm run setup
```

### Docker (macOS/Linux)

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/wonderwhy-er/DesktopCommanderMCP/refs/heads/main/install-docker.sh)
```

## Конфигурация

### Ручная конфигурация Claude Desktop

```json
{
  "mcpServers": {
    "desktop-commander": {
      "command": "npx",
      "args": [
        "-y",
        "@wonderwhy-er/desktop-commander@latest"
      ]
    }
  }
}
```

### Базовая настройка Docker

```json
{
  "mcpServers": {
    "desktop-commander-in-docker": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "mcp/desktop-commander:latest"
      ]
    }
  }
}
```

### Docker с монтированием папок

```json
{
  "mcpServers": {
    "desktop-commander-in-docker": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-v", "/Users/username/Desktop:/mnt/desktop",
        "-v", "/Users/username/Documents:/mnt/documents",
        "mcp/desktop-commander:latest"
      ]
    }
  }
}
```

## Возможности

- Расширенные команды терминала с интерактивным управлением процессами
- Выполнение кода в памяти (Python, Node.js, R) без сохранения файлов
- Мгновенный анализ данных - просто попросите проанализировать CSV/JSON файлы
- Взаимодействие с запущенными процессами (SSH, базы данных, серверы разработки)
- Выполнение команд терминала с потоковым выводом
- Поддержка тайм-аутов команд и фонового выполнения
- Управление процессами (список и завершение процессов)
- Управление сессиями для долго выполняющихся команд
- Управление конфигурацией сервера с динамическими изменениями
- Полные операции с файловой системой (чтение/запись файлов, создание/список директорий, перемещение файлов, поиск файлов, получение метаданных)

## Примеры использования

```
Analyze this CSV file
```

```
Run a development server in the background
```

```
Search for all TODO comments in my codebase
```

```
Execute Python code to process this data
```

```
Connect to my remote server via SSH
```

## Ресурсы

- [GitHub Repository](https://github.com/wonderwhy-er/DesktopCommanderMCP)

## Примечания

Desktop Commander предлагает автоматические обновления для большинства методов установки (npx, bash установщик, Smithery, ручная конфигурация и Docker). Только локальная загрузка требует ручного обновления. Сервер включает комплексную поддержку удаления с автоматическим резервным копированием и возможностями восстановления. Установка Docker обеспечивает полную изоляцию с постоянными средами разработки.