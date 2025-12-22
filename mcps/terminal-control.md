---
title: Terminal-Control MCP сервер
description: MCP сервер, который обеспечивает безопасное выполнение команд терминала, навигацию по директориям и операции с файловой системой через стандартизированный интерфейс со встроенными мерами безопасности и кроссплатформенной поддержкой.
tags:
- DevOps
- Code
- Productivity
- Security
author: GongRzhe
featured: false
---

MCP сервер, который обеспечивает безопасное выполнение команд терминала, навигацию по директориям и операции с файловой системой через стандартизированный интерфейс со встроенными мерами безопасности и кроссплатформенной поддержкой.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @GongRzhe/terminal-controller-mcp --client claude
```

### PyPI

```bash
pip install terminal-controller
```

### UV

```bash
uv pip install terminal-controller
```

### Из исходного кода

```bash
git clone https://github.com/GongRzhe/terminal-controller-mcp.git
cd terminal-controller-mcp
python setup_mcp.py
```

## Конфигурация

### Claude Desktop (UVX)

```json
"terminal-controller": {
  "command": "uvx",
  "args": ["terminal_controller"]
}
```

### Claude Desktop (Python)

```json
"terminal-controller": {
  "command": "python",
  "args": ["-m", "terminal_controller"]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `execute_command` | Выполняет команду терминала и возвращает результаты с контролем таймаута |
| `get_command_history` | Получает историю недавно выполненных команд |
| `get_current_directory` | Получает текущую рабочую директорию |
| `change_directory` | Изменяет текущую рабочую директорию |
| `list_directory` | Выводит список файлов и поддиректорий в указанной директории |
| `write_file` | Записывает содержимое в файл с опциями перезаписи или добавления |
| `read_file` | Читает содержимое файла с опциональным выбором строк |
| `insert_file_content` | Вставляет содержимое в определенную строку(и) файла |
| `delete_file_content` | Удаляет содержимое из определенной строки(строк) файла |
| `update_file_content` | Обновляет содержимое в определенной строке(строках) файла |

## Возможности

- Выполнение команд с контролем таймаута и всесторонним захватом вывода
- Управление директориями с возможностями навигации и листинга
- Меры безопасности со встроенными защитными механизмами против опасных команд
- Отслеживание истории команд и отображение недавних выполнений
- Кроссплатформенная поддержка для Windows и UNIX-систем
- Файловые операции с возможностями чтения, записи, обновления, вставки и удаления с точностью до строки

## Примеры использования

```
Run the command `ls -la` in the current directory
```

```
Navigate to my Documents folder
```

```
Show me the contents of my Downloads directory
```

```
Show me my recent command history
```

```
Read the content of config.json
```

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/terminal-controller-mcp)

## Примечания

Требует Python 3.11+ и реализует меры безопасности, включая контроль таймаута, черный список опасных команд и правильную обработку ошибок. Пути конфигурации различаются в зависимости от ОС: macOS (~/.../Claude/claude_desktop_config.json) и Windows (%APPDATA%\Claude\claude_desktop_config.json).