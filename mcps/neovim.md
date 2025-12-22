---
title: Neovim MCP сервер
description: MCP сервер, который соединяет Claude Desktop с Neovim, используя официальную JavaScript библиотеку neovim/node-client. Позволяет редактировать текст с помощью ИИ через нативные команды и рабочие процессы Vim.
tags:
- Code
- Productivity
- AI
- Integration
author: Community
featured: false
---

MCP сервер, который соединяет Claude Desktop с Neovim, используя официальную JavaScript библиотеку neovim/node-client. Позволяет редактировать текст с помощью ИИ через нативные команды и рабочие процессы Vim.

## Установка

### DXT пакет (рекомендуется)

```bash
1. Download the latest .dxt file from Releases
2. Drag the file to Claude Desktop
```

### NPX

```bash
npx -y mcp-neovim-server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "MCP Neovim Server": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-neovim-server"
      ],
      "env": {
        "ALLOW_SHELL_COMMANDS": "true",
        "NVIM_SOCKET_PATH": "/tmp/nvim"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `vim_buffer` | Получить содержимое буфера с номерами строк (поддерживает параметр filename) |
| `vim_command` | Отправить команду в VIM для навигации, точечного редактирования и удаления строк |
| `vim_status` | Получить полный статус Neovim включая позицию курсора, режим, имя файла, визуальное выделение, окн... |
| `vim_edit` | Редактировать строки используя режимы insert, replace или replaceAll |
| `vim_window` | Управлять окнами Neovim (split, vsplit, close, navigate) |
| `vim_mark` | Установить именованные метки в определенных позициях |
| `vim_register` | Установить содержимое регистров |
| `vim_visual` | Создать выделения в визуальном режиме |
| `vim_buffer_switch` | Переключаться между буферами по имени или номеру |
| `vim_buffer_save` | Сохранить текущий буфер или сохранить в определенный файл |
| `vim_file_open` | Открыть файлы в новые буферы |
| `vim_search` | Поиск в текущем буфере с поддержкой regex |
| `vim_search_replace` | Найти и заменить с расширенными опциями |
| `vim_grep` | Поиск по всему проекту используя vimgrep с quickfix списком |
| `vim_macro` | Записать, остановить и воспроизвести Vim макросы |

## Возможности

- Подключается к вашему экземпляру nvim если вы открыли файл сокета
- Просматривает ваши текущие буферы и управляет переключением буферов
- Получает местоположение курсора, режим, имя файла, метки, регистры и визуальные выделения
- Выполняет vim команды и опционально shell команды через vim
- Может делать правки используя режимы insert, replace или replaceAll
- Функциональность поиска и замены с поддержкой regex
- Поиск grep по всему проекту с интеграцией quickfix
- Комплексное управление окнами
- Мониторинг состояния и диагностика соединения

## Переменные окружения

### Опциональные
- `ALLOW_SHELL_COMMANDS` - Установите в 'true' чтобы включить выполнение shell команд (например `!ls`). По умолчанию false для безопасности.
- `NVIM_SOCKET_PATH` - Установите путь к вашему Neovim сокету. По умолчанию '/tmp/nvim' если не указано.

## Примеры использования

```
Get contextual help and guidance for common Neovim workflows including editing, navigation, search, buffer management, window operations, and macro usage
```

## Ресурсы

- [GitHub Repository](https://github.com/bigcodegen/mcp-neovim-server)

## Примечания

Требует запуска nvim с открытым сокетом (например, --listen /tmp/nvim). Может плохо взаимодействовать со сложными конфигурациями neovim или плагинами. Требуется соединение через сокет - не будет работать со стандартным vim. Реализует комплексную обработку ошибок с пользовательскими классами ошибок.