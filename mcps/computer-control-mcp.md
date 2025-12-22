---
title: computer-control-mcp MCP сервер
description: MCP сервер, который предоставляет возможности управления компьютером, включая работу с мышью, клавиатурой, OCR и управление экраном, используя PyAutoGUI, RapidOCR, ONNXRuntime без внешних зависимостей.
tags:
- Productivity
- AI
- API
- Integration
author: Community
featured: false
---

MCP сервер, который предоставляет возможности управления компьютером, включая работу с мышью, клавиатурой, OCR и управление экраном, используя PyAutoGUI, RapidOCR, ONNXRuntime без внешних зависимостей.

## Установка

### UVX

```bash
uvx computer-control-mcp@latest
```

### Глобальная установка через Pip

```bash
pip install computer-control-mcp
computer-control-mcp
```

### Из исходного кода

```bash
git clone https://github.com/AB498/computer-control-mcp.git
cd computer-control-mcp
pip install -e .
python -m computer_control_mcp.core
```

### Сборка с Hatch

```bash
pip install hatch
hatch build
pip install dist/*.whl --upgrade
computer-control-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "computer-control-mcp": {
      "command": "uvx",
      "args": ["computer-control-mcp@latest"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `click_screen` | Клик по указанным координатам экрана |
| `move_mouse` | Перемещение курсора мыши к указанным координатам |
| `drag_mouse` | Перетаскивание мыши из одной позиции в другую |
| `mouse_down` | Удерживание кнопки мыши ('left', 'right', 'middle') |
| `mouse_up` | Отпускание кнопки мыши ('left', 'right', 'middle') |
| `type_text` | Ввод указанного текста в текущей позиции курсора |
| `press_key` | Нажатие указанной клавиши |
| `key_down` | Удерживание определенной клавиши до отпускания |
| `key_up` | Отпускание определенной клавиши |
| `press_keys` | Нажатие клавиш (поддерживает отдельные клавиши, последовательности и комбинации) |
| `take_screenshot` | Захват экрана или окна с опциональным сохранением в папку загрузок |
| `take_screenshot_with_ocr` | Извлечение и возврат текста с координатами через OCR с экрана или окна |
| `get_screen_size` | Получение текущего разрешения экрана |
| `list_windows` | Список всех открытых окон |
| `activate_window` | Перевод указанного окна на передний план |

## Возможности

- Управление движением мыши и кликами
- Ввод текста в текущей позиции курсора
- Создание скриншотов всего экрана или конкретных окон с опциональным сохранением в папку загрузок
- Извлечение текста из скриншотов с помощью OCR (оптическое распознавание символов)
- Просмотр и активация окон
- Нажатие клавиш
- Операции перетаскивания

## Ресурсы

- [GitHub Repository](https://github.com/AB498/computer-control-mcp)

## Примечания

Запуск uvx computer-control-mcp@latest в первый раз загрузит python зависимости (около 70MB), что может занять некоторое время. Рекомендуется запустить это в терминале перед использованием в качестве MCP. Последующие запуски будут мгновенными.