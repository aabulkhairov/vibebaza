---
title: code-executor MCP сервер
description: MCP сервер, который позволяет LLM выполнять Python код в указанном Python окружении (Conda, virtualenv, или UV virtualenv) с поддержкой инкрементной генерации кода для обработки больших блоков кода.
tags:
- Code
- AI
- DevOps
- Productivity
- Integration
author: Community
featured: false
---

MCP сервер, который позволяет LLM выполнять Python код в указанном Python окружении (Conda, virtualenv, или UV virtualenv) с поддержкой инкрементной генерации кода для обработки больших блоков кода.

## Установка

### Из исходного кода

```bash
git clone https://github.com/bazinga012/mcp_code_executor.git
cd mcp_code_executor
npm install
npm run build
```

### Docker

```bash
docker run -i --rm mcp-code-executor
```

## Конфигурация

### Node.js

```json
{
  "mcpServers": {
    "mcp-code-executor": {
      "command": "node",
      "args": [
        "/path/to/mcp_code_executor/build/index.js" 
      ],
      "env": {
        "CODE_STORAGE_DIR": "/path/to/code/storage",
        "ENV_TYPE": "conda",
        "CONDA_ENV_NAME": "your-conda-env"
      }
    }
  }
}
```

### Docker

```json
{
  "mcpServers": {
    "mcp-code-executor": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "mcp-code-executor"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `execute_code` | Выполняет Python код в настроенном окружении. Лучше всего подходит для коротких фрагментов кода. |
| `install_dependencies` | Устанавливает Python пакеты в окружение. |
| `check_installed_packages` | Проверяет, установлены ли уже пакеты в окружении. |
| `configure_environment` | Динамически изменяет конфигурацию окружения. |
| `get_environment_config` | Получает текущую конфигурацию окружения. |
| `initialize_code_file` | Создает новый Python файл с начальным содержимым. Используйте это как первый шаг для более длинного кода... |
| `append_to_code_file` | Добавляет содержимое к существующему Python файлу кода. Используйте это для добавления кода к файлу, созданному с помощью... |
| `execute_code_file` | Выполняет существующий Python файл. Используйте это как финальный шаг после создания кода с помощью инициализации... |
| `read_code_file` | Читает содержимое существующего Python файла кода. Используйте это для проверки текущего состояния файла... |

## Возможности

- Выполнение Python кода из промптов LLM
- Поддержка инкрементной генерации кода для преодоления ограничений токенов
- Запуск кода в указанном окружении (Conda, virtualenv, или UV virtualenv)
- Установка зависимостей при необходимости
- Проверка уже установленных пакетов
- Динамическая настройка окружения во время выполнения
- Настраиваемая директория хранения кода

## Переменные окружения

### Обязательные
- `CODE_STORAGE_DIR` - Директория, где будет храниться сгенерированный код
- `ENV_TYPE` - Тип окружения (conda, venv, или venv-uv)

### Опциональные
- `CONDA_ENV_NAME` - Имя Conda окружения для использования (когда ENV_TYPE равно conda)
- `VENV_PATH` - Путь к директории virtualenv (когда ENV_TYPE равно venv)
- `UV_VENV_PATH` - Путь к директории UV virtualenv (когда ENV_TYPE равно venv-uv)

## Примеры использования

```
Выполните Python код для генерации случайных матриц с помощью numpy
```

```
Установите Python пакеты такие как pandas и matplotlib
```

```
Проверьте какие пакеты установлены в окружении
```

```
Создайте сложные многокомпонентные Python приложения используя инкрементную генерацию кода
```

```
Запустите скрипты анализа данных с доступом к библиотекам научных вычислений
```

## Ресурсы

- [GitHub Repository](https://github.com/bazinga012/mcp_code_executor)

## Примечания

Конфигурация Docker протестирована только с типом окружения venv-uv. Другие типы окружения могут потребовать дополнительной настройки. Этот пакет поддерживает обратную совместимость с более ранними версиями.