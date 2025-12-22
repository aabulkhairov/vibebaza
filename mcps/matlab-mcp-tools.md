---
title: Matlab-MCP-Tools MCP сервер
description: MCP сервер, который предоставляет инструменты для разработки и выполнения MATLAB файлов,
  включая выполнение скриптов, поддержку контекста рабочего пространства, захват графиков и
  выполнение отдельных секций MATLAB кода.
tags:
- Code
- Analytics
- Productivity
- Integration
author: neuromechanist
featured: false
---

MCP сервер, который предоставляет инструменты для разработки и выполнения MATLAB файлов, включая выполнение скриптов, поддержку контекста рабочего пространства, захват графиков и выполнение отдельных секций MATLAB кода.

## Установка

### Быстрый старт (Рекомендуется)

```bash
./install-matlab-mcp.sh
```

### Расширенная установка

```bash
git clone [repository-url]
cd matlab-mcp-tools
export MATLAB_PATH=/path/to/your/matlab/installation
./install-matlab-mcp.sh
```

### Устаревший способ установки (Ручной)

```bash
# Install uv using Homebrew
brew install uv
# OR install using pip
pip install uv

# For macOS
export MATLAB_PATH=/Applications/MATLAB_R2024b.app
# For Windows
export MATLAB_PATH="C:/Program Files/MATLAB/R2024b"

./scripts/setup-matlab-mcp.sh
cp mcp-pip.json ~/.cursor/mcp.json
```

## Конфигурация

### Конфигурация MCP

```json
{
  "mcpServers": {
    "matlab": {
      "command": "matlab-mcp-server",
      "args": [],
      "env": {
        "MATLAB_PATH": "${MATLAB_PATH}",
        "PATH": "${MATLAB_PATH}/bin:${PATH}"
      },
      "disabled": false,
      "autoApprove": [
        "list_tools",
        "get_script_sections"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `execute_script` | Выполнить MATLAB код или файл скрипта |
| `execute_script_section` | Выполнить определенные секции MATLAB скрипта |
| `get_script_sections` | Получить информацию о секциях скрипта |
| `create_matlab_script` | Создать новый MATLAB скрипт |
| `get_workspace` | Получить текущие переменные рабочего пространства MATLAB |

## Возможности

- Выполнение полных MATLAB скриптов
- Выполнение отдельных секций скриптов
- Поддержка контекста рабочего пространства между выполнениями
- Захват и отображение графиков
- Поддержка режима ячеек (секции, разделенные %%)
- Автоопределение установок MATLAB
- Автоустановка менеджера пакетов UV
- Автоматическое генерирование конфигурации MCP
- Обработка ошибок с подробными сообщениями об ошибках

## Переменные окружения

### Опциональные
- `MATLAB_PATH` - Путь к директории установки MATLAB

## Примеры использования

```
Execute a MATLAB script that generates a sine wave plot
```

```
Run specific sections of a MATLAB file for data analysis
```

```
Generate sample data and calculate basic statistics
```

```
Create visualizations with subplots and histograms
```

```
Maintain workspace variables between script executions
```

## Ресурсы

- [GitHub Repository](https://github.com/neuromechanist/matlab-mcp-tools)

## Примечания

Требует Python 3.10+, MATLAB с установленным Python Engine и менеджер пакетов uv. Установщик сокращает время настройки с 15+ минут до ~2 минут благодаря функциям автоопределения. Выходные файлы сохраняются в директориях matlab_output и test_output.