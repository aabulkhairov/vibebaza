---
title: QGIS MCP сервер
description: Подключает QGIS к Claude AI через Model Context Protocol, обеспечивая создание проектов с помощью промптов, загрузку слоёв, выполнение кода и прямое управление QGIS из Claude.
tags:
- Integration
- Code
- Productivity
- AI
- Analytics
author: jjsantos01
featured: true
---

Подключает QGIS к Claude AI через Model Context Protocol, обеспечивая создание проектов с помощью промптов, загрузку слоёв, выполнение кода и прямое управление QGIS из Claude.

## Установка

### Из исходного кода

```bash
git clone git@github.com:jjsantos01/qgis_mcp.git

# Install uv package manager (Mac):
brew install uv

# Install uv package manager (Windows):
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# Copy qgis_mcp_plugin folder to QGIS plugins directory:
# Windows: C:\Users\USER\AppData\Roaming\QGIS\QGIS3\profiles\default\python\plugins
# MacOS: ~/Library/Application\ Support/QGIS/QGIS3/profiles/default/python/plugins
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "qgis": {
            "command": "uv",
            "args": [
                "--directory",
                "/ABSOLUTE/PATH/TO/PARENT/REPO/FOLDER/qgis_mcp/src/qgis_mcp",
                "run",
                "qgis_mcp_server.py"
            ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `ping` | Простая команда ping для проверки подключения к серверу |
| `get_qgis_info` | Получить информацию о текущей установке QGIS |
| `load_project` | Загрузить проект QGIS по указанному пути |
| `create_new_project` | Создать новый проект и сохранить его |
| `get_project_info` | Получить информацию о текущем проекте |
| `add_vector_layer` | Добавить векторный слой в проект |
| `add_raster_layer` | Добавить растровый слой в проект |
| `get_layers` | Получить все слои текущего проекта |
| `remove_layer` | Удалить слой из проекта по его ID |
| `zoom_to_layer` | Масштабировать до границ указанного слоя |
| `get_layer_features` | Получить объекты из векторного слоя с опциональным ограничением |
| `execute_processing` | Выполнить алгоритм обработки с заданными параметрами |
| `save_project` | Сохранить текущий проект по указанному пути |
| `render_map` | Отрендерить текущий вид карты в файл изображения |
| `execute_code` | Выполнить произвольный код PyQGIS, переданный как строка |

## Возможности

- Двухсторонняя связь между Claude AI и QGIS через сервер на основе сокетов
- Управление проектами: создание, загрузка и сохранение проектов в QGIS
- Управление слоями: добавление и удаление векторных или растровых слоёв в проект
- Выполнение алгоритмов обработки из Processing Toolbox
- Запуск произвольного Python кода в QGIS из Claude

## Примеры использования

```
Ping для проверки соединения, создание нового проекта, загрузка векторных и растровых слоёв, масштабирование до слоёв, выполнение алгоритмов центроидов, создание хороплетных карт с методами классификации, рендеринг карт в файлы изображений и сохранение проектов
```

## Ресурсы

- [GitHub Repository](https://github.com/jjsantos01/qgis_mcp)

## Примечания

Требует QGIS 3.X (протестировано на 3.22), Claude desktop, Python 3.10+ и менеджер пакетов uv. Система состоит из плагина QGIS, создающего сокет-сервер, и MCP сервера, реализующего Model Context Protocol. Основан на проекте BlenderMCP от Siddharth Ahuja. Инструмент выполнения кода мощный, но требует осторожности.