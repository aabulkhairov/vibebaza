---
title: ESP MCP сервер
description: MCP сервер, который объединяет команды ESP-IDF для сборки, прошивки и управления проектами ESP32/ESP устройств через взаимодействие с LLM.
tags:
- DevOps
- Code
author: Community
featured: false
---

MCP сервер, который объединяет команды ESP-IDF для сборки, прошивки и управления проектами ESP32/ESP устройств через взаимодействие с LLM.

## Установка

### Из исходного кода

```bash
git clone git@github.com:horw/esp-mcp.git
```

## Конфигурация

### Конфигурация MCP сервера

```json
{
    "mcpServers": {
        "esp-run": {
            "command": "<path_to_uv_or_python_executable>",
            "args": [
                "--directory",
                "<path_to_cloned_esp-mcp_repository>",
                "run",
                "main.py"
            ],
            "env": {
                "IDF_PATH": "<path_to_your_esp-idf_directory>"
            }
        }
    }
}
```

## Возможности

- Поддерживает базовые команды сборки проектов ESP-IDF
- Прошивка собранной прошивки на подключенные ESP устройства с опциональным указанием порта
- Экспериментальная поддержка автоматического исправления проблем на основе логов сборки
- Объединяет ESP-IDF и связанные команды проекта в одном месте
- Упрощает начало работы, используя только взаимодействие с LLM

## Переменные окружения

### Обязательные
- `IDF_PATH` - Должен указывать на корневую директорию вашей установки ESP-IDF

## Примеры использования

```
Build the project located at `/path/to/my/esp-project` using the `esp-mcp`
```

```
Clean the build files for the ESP32 project in the `examples/hello_world` directory
```

```
Flash the firmware to my connected ESP32 device for the project in `my_app`
```

## Ресурсы

- [GitHub Repository](https://github.com/horw/esp-mcp)

## Примечания

Этот проект в настоящее время является Proof of Concept (PoC). Планы на будущее включают расширенную поддержку команд ESP-IDF (monitor, menuconfig), управление устройствами и интеграцию с другими инструментами и платформами разработки встраиваемых систем. Требует отдельной установки ESP-IDF.