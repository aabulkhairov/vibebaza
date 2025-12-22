---
title: Jupyter Notebook MCP сервер
description: JupyterMCP соединяет Jupyter Notebook с Claude AI через Model Context Protocol (MCP), позволяя Claude напрямую взаимодействовать и управлять Jupyter Notebooks для выполнения кода с помощью AI, анализа данных и визуализации.
tags:
- Analytics
- Code
- AI
- Integration
- Productivity
author: jjsantos01
featured: true
---

JupyterMCP соединяет Jupyter Notebook с Claude AI через Model Context Protocol (MCP), позволяя Claude напрямую взаимодействовать и управлять Jupyter Notebooks для выполнения кода с помощью AI, анализа данных и визуализации.

## Установка

### Из исходного кода

```bash
git clone https://github.com/jjsantos01/jupyter-notebook-mcp.git
uv run python -m ipykernel install --name jupyter-mcp
```

### Запуск Jupyter

```bash
uv run jupyter nbclassic
```

### Инициализация WebSocket сервера

```bash
import sys
sys.path.append('/path/to/jupyter-notebook-mcp/src')

from jupyter_ws_server import setup_jupyter_mcp_integration

# Start the WebSocket server inside Jupyter
server, port = setup_jupyter_mcp_integration()
```

## Конфигурация

### Claude Desktop

```json
{
 "mcpServers": {
     "jupyter": {
         "command": "uv",
         "args": [
             "--directory",
             "/ABSOLUTE/PATH/TO/PARENT/REPO/FOLDER/src",
             "run",
             "jupyter_mcp_server.py"
         ]
     }
 }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `ping` | Проверить подключение к серверу |
| `insert_and_execute_cell` | Вставить ячейку в указанную позицию и выполнить её |
| `save_notebook` | Сохранить текущий Jupyter ноутбук |
| `get_cells_info` | Получить информацию обо всех ячейках в ноутбуке |
| `get_notebook_info` | Получить информацию о текущем ноутбуке |
| `run_cell` | Запустить конкретную ячейку по её индексу |
| `run_all_cells` | Запустить все ячейки в ноутбуке |
| `get_cell_text_output` | Получить текстовый вывод определенной ячейки |
| `get_image_output` | Получить изображения из вывода определенной ячейки |
| `edit_cell_content` | Редактировать содержимое существующей ячейки |
| `set_slideshow_type` | Установить тип слайд-шоу для ячейки |

## Возможности

- Двусторонняя связь: Подключает Claude AI к Jupyter Notebook через WebSocket-сервер
- Управление ячейками: Вставка, выполнение и управление ячейками ноутбука
- Управление ноутбуками: Сохранение ноутбуков и получение информации о ноутбуке
- Выполнение ячеек: Запуск отдельных ячеек или выполнение всех ячеек в ноутбуке
- Получение результатов: Извлечение содержимого вывода из выполненных ячеек с опциями ограничения текста

## Примеры использования

```
You have access to a Jupyter Notebook server. I need to create a presentation about Python's Seaborn library. The content is as follows: - What is Seaborn? - Long vs. Wide data format - Advantages of Seaborn over Matplotlib - Commonly used Seaborn functions - Live demonstration (comparison of Seaborn vs. Matplotlib)
```

```
You have access to a Jupyter Notebook server. By default it runs Python, but you can run Stata (v18) code in this server using the %%stata magic. Run the available tools to solve the exercise, execute the code, and interpret the results.
```

## Ресурсы

- [GitHub Repository](https://github.com/jjsantos01/jupyter-notebook-mcp)

## Примечания

⚠️ Совместим ТОЛЬКО с Jupyter Notebook версии 6.x. НЕ работает с Jupyter Lab, Jupyter Notebook v7.x, VS Code Notebooks, Google Colab или другими интерфейсами ноутбуков. Это экспериментальный проект, который выполняет произвольный Python код, поэтому следует использовать с осторожностью. Текстовый вывод ячеек по умолчанию ограничен 1500 символами.