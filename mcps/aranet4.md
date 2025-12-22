---
title: Aranet4 MCP сервер
description: MCP сервер для управления вашим CO2 датчиком Aranet4, получения данных с устройства через Bluetooth и их хранения в локальной SQLite базе данных для отслеживания и запроса исторических измерений.
tags:
- Monitoring
- Database
- Analytics
- Integration
author: Community
featured: false
---

MCP сервер для управления вашим CO2 датчиком Aranet4, получения данных с устройства через Bluetooth и их хранения в локальной SQLite базе данных для отслеживания и запроса исторических измерений.

## Установка

### Из исходного кода (с uv)

```bash
git clone git@github.com:diegobit/aranet4-mcp-server.git
cd aranet4-mcp-server
```

### Из исходного кода (с pip)

```bash
git clone git@github.com:diegobit/aranet4-mcp-server.git
cd aranet4-mcp-server
pip install .
```

### Docker

```bash
Dockerfile is available. Remember to pass env variables or update config.yaml.
```

## Конфигурация

### Claude Desktop

```json
"aranet4": {
  "command": "{{PATH_TO_UV}}",
  "args": [
    "--directory",
    "{{PATH_TO_SRC}}/aranet4-mcp-server/",
    "run",
    "src/server.py"
  ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `init_aranet4_config` | Помощь в настройке устройства |
| `scan_devices` | Сканирование ближайших bluetooth устройств aranet4 |
| `get_configuration_and_db_stats` | Получение текущего config.yaml и общей статистики из локальной sqlite3 базы данных |
| `set_configuration` | Установка значений в config.yaml |
| `fetch_new_data` | Получение новых данных с настроенного ближайшего устройства aranet4 и сохранение в локальную базу данных |
| `get_recent_data` | Получение последних данных из локальной базы данных. Можно указать количество измерений |
| `get_data_by_timerange` | Получение данных за определенный временной период из локальной базы данных. Можно указать количество измерений |

## Возможности

- Сканирование ближайших устройств Aranet4
- Получение новых данных из памяти встроенного устройства и сохранение в локальную SQLite базу данных
- Запросы о последних измерениях или конкретных прошлых датах
- Генерация графиков данных для визуализации (для MCP клиентов, которые поддерживают изображения)
- Помощь в настройке с руководством AI
- Автоматическое получение данных с поддержкой cronjob/launch agent

## Примеры использования

```
init aranet4
```

```
Ask questions about recent measurements or about a specific past date
```

```
Ask data to be plotted to also have a nice visualization
```

## Ресурсы

- [GitHub Repository](https://github.com/diegobit/aranet4-mcp-server)

## Примечания

Требует устройство Aranet4, уже сопряженное через BLE. На MacOS используйте LightBlue из App Store для сопряжения. Пути конфигурации: Claude Desktop MacOS: ~/Library/Application Support/Claude/claude_desktop_config.json, Cursor MacOS: ~/.cursor/mcp.json. Построен на основе библиотеки Aranet4-Python.