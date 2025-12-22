---
title: MCP-NixOS MCP сервер
description: MCP сервер, который предоставляет AI ассистентам точную информацию в реальном времени о NixOS пакетах (130K+), опциях конфигурации (22K+), настройках Home Manager (4K+), конфигурациях nix-darwin (1K+) и истории версий пакетов.
tags:
- DevOps
- Search
- API
- Code
- Productivity
author: utensils
featured: true
---

MCP сервер, который предоставляет AI ассистентам точную информацию в реальном времени о NixOS пакетах (130K+), опциях конфигурации (22K+), настройках Home Manager (4K+), конфигурациях nix-darwin (1K+) и истории версий пакетов.

## Установка

### UVX (Рекомендуется)

```bash
uvx mcp-nixos
```

### Nix

```bash
nix run github:utensils/mcp-nixos
```

### Docker

```bash
docker run --rm -i ghcr.io/utensils/mcp-nixos
```

### Pip

```bash
pip install mcp-nixos
```

### UV Pip

```bash
uv pip install mcp-nixos
```

## Конфигурация

### Конфигурация UVX

```json
{
  "mcpServers": {
    "nixos": {
      "command": "uvx",
      "args": ["mcp-nixos"]
    }
  }
}
```

### Конфигурация Nix

```json
{
  "mcpServers": {
    "nixos": {
      "command": "nix",
      "args": ["run", "github:utensils/mcp-nixos", "--"]
    }
  }
}
```

### Конфигурация Docker

```json
{
  "mcpServers": {
    "nixos": {
      "command": "docker",
      "args": ["run", "--rm", "-i", "ghcr.io/utensils/mcp-nixos"]
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "nixos": {
      "type": "stdio",
      "command": "uv",
      "args": [
        "run",
        "--directory",
        "/home/hackerman/Projects/mcp-nixos",
        "mcp-nixos"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `nixos_search` | Поиск пакетов, опций или программ по запросу, типу и каналу |
| `nixos_info` | Получение подробной информации о пакетах или опциях |
| `nixos_stats` | Получение количества пакетов и опций для канала |
| `nixos_channels` | Список всех доступных каналов NixOS |
| `nixos_flakes_search` | Поиск по флейкам сообщества |
| `nixos_flakes_stats` | Получение статистики экосистемы флейков |
| `nixhub_package_versions` | Получение истории версий пакетов с хэшами коммитов |
| `nixhub_find_version` | Умный поиск конкретных версий пакетов |
| `home_manager_search` | Поиск опций конфигурации пользователя Home Manager |
| `home_manager_info` | Получение подробностей опций Home Manager с предложениями |
| `home_manager_stats` | Просмотр доступных опций Home Manager |
| `home_manager_list_options` | Обзор всех 131 категории Home Manager |
| `home_manager_options_by_prefix` | Изучение опций Home Manager по префиксу |
| `darwin_search` | Поиск опций конфигурации nix-darwin для macOS |
| `darwin_info` | Получение подробностей опций nix-darwin |

## Возможности

- Доступ к более чем 130К пакетов NixOS с данными в реальном времени
- Более 22К опций конфигурации NixOS
- Более 4К настроек Home Manager для пользовательских конфигураций
- Более 1К опций конфигурации nix-darwin для macOS
- История версий пакетов через NixHub.io с хэшами коммитов
- Кроссплатформенная поддержка (Windows, macOS, Linux) — установка Nix не требуется
- Работа без состояния, без кэширования или необходимости очистки файлов
- Умные предложения при опечатках в именах опций
- Динамическое разрешение каналов с отслеживанием стабильных каналов
- Поиск флейков сообщества и статистика

## Переменные окружения

### Опциональные
- `ELASTICSEARCH_URL` - Эндпоинт NixOS API

## Примеры использования

```
Найти пакеты, связанные с разработкой на Python
```

```
Получить опции конфигурации для настройки веб-сервера
```

```
Найти опции Home Manager для настройки пользовательских dotfiles
```

```
Найти специфичные для macOS настройки nix-darwin
```

```
Посмотреть историю версий конкретного пакета
```

## Ресурсы

- [GitHub Repository](https://github.com/utensils/mcp-nixos)

## Примечания

Работает на любой системе без требования установки Nix/NixOS. Версия 1.0.0 была полностью переписана с упрощением кодовой базы, а версия 1.0.1 добавила поддержку async. При ошибках песочницы Nix запускайте с 'nix run --option sandbox relaxed'. Инструмент запрашивает данные в реальном времени из API NixHub.io и search.nixos.org.