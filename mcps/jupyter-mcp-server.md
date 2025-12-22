---
title: Jupyter MCP Server MCP сервер
description: MCP сервер, который позволяет ИИ подключаться к Jupyter Notebook и управлять ими в реальном времени, обеспечивая выполнение кода, манипулирование ячейками и поддержку мультимодального вывода в любом развертывании Jupyter.
tags:
- Code
- Analytics
- AI
- Productivity
- Integration
author: datalayer
featured: true
---

MCP сервер, который позволяет ИИ подключаться к Jupyter Notebook и управлять ими в реальном времени, обеспечивая выполнение кода, манипулирование ячейками и поддержку мультимодального вывода в любом развертывании Jupyter.

## Установка

### Настройка окружения

```bash
pip install jupyterlab==4.4.1 jupyter-collaboration==4.0.2 jupyter-mcp-tools>=0.1.4 ipykernel
pip uninstall -y pycrdt datalayer_pycrdt
pip install datalayer_pycrdt==0.12.17
```

### Запуск JupyterLab

```bash
jupyter lab --port 8888 --IdentityProvider.token MY_TOKEN --ip 0.0.0.0
```

### Установка UV

```bash
pip install uv
uv --version
```

## Конфигурация

### Конфигурация UVX

```json
{
  "mcpServers": {
    "jupyter": {
      "command": "uvx",
      "args": ["jupyter-mcp-server@latest"],
      "env": {
        "JUPYTER_URL": "http://localhost:8888",
        "JUPYTER_TOKEN": "MY_TOKEN",
        "ALLOW_IMG_OUTPUT": "true"
      }
    }
  }
}
```

### Docker macOS/Windows

```json
{
  "mcpServers": {
    "jupyter": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm",
        "-e", "JUPYTER_URL",
        "-e", "JUPYTER_TOKEN",
        "-e", "ALLOW_IMG_OUTPUT",
        "datalayer/jupyter-mcp-server:latest"
      ],
      "env": {
        "JUPYTER_URL": "http://host.docker.internal:8888",
        "JUPYTER_TOKEN": "MY_TOKEN",
        "ALLOW_IMG_OUTPUT": "true"
      }
    }
  }
}
```

### Docker Linux

```json
{
  "mcpServers": {
    "jupyter": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm",
        "-e", "JUPYTER_URL",
        "-e", "JUPYTER_TOKEN",
        "-e", "ALLOW_IMG_OUTPUT",
        "--network=host",
        "datalayer/jupyter-mcp-server:latest"
      ],
      "env": {
        "JUPYTER_URL": "http://localhost:8888",
        "JUPYTER_TOKEN": "MY_TOKEN",
        "ALLOW_IMG_OUTPUT": "true"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_files` | Список файлов и директорий в файловой системе Jupyter сервера |
| `list_kernels` | Список всех доступных и запущенных сессий ядер на Jupyter сервере |
| `use_notebook` | Подключение к файлу блокнота, создание нового или переключение между блокнотами |
| `list_notebooks` | Список всех блокнотов, доступных на Jupyter сервере, и их статус |
| `restart_notebook` | Перезапуск ядра для определенного управляемого блокнота |
| `unuse_notebook` | Отключение от определенного блокнота и освобождение его ресурсов |
| `read_notebook` | Чтение исходного содержимого ячеек блокнота с опциями краткого или подробного формата |
| `read_cell` | Чтение полного содержимого (метаданные, исходник и вывод) одной ячейки |
| `insert_cell` | Вставка новой ячейки кода или markdown в указанную позицию |
| `delete_cell` | Удаление ячейки по указанному индексу |
| `overwrite_cell_source` | Перезапись исходного кода существующей ячейки |
| `execute_cell` | Выполнение ячейки с таймаутом, поддерживает мультимодальный вывод включая изображения |
| `insert_execute_code_cell` | Вставка новой ячейки кода и её выполнение за один шаг |
| `execute_code` | Выполнение кода напрямую в ядре, поддерживает магические команды и команды shell |
| `notebook_run-all-cells` | Последовательное выполнение всех ячеек в текущем блокноте |

## Возможности

- Управление в реальном времени: мгновенный просмотр изменений в блокноте по мере их происхождения
- Умное выполнение: автоматическая адаптация при сбое выполнения ячейки благодаря обратной связи с выводом ячейки
- Контекстная осведомленность: понимание полного контекста блокнота для более релевантных взаимодействий
- Мультимодальная поддержка: поддержка различных типов вывода, включая изображения, графики и текст
- Поддержка нескольких блокнотов: плавное переключение между несколькими блокнотами
- Интеграция с JupyterLab: расширенная интеграция с UI, например автоматическое открытие блокнотов
- MCP-совместимость: работает с любым MCP клиентом, таким как Claude Desktop, Cursor, Windsurf и другими

## Переменные окружения

### Обязательные
- `JUPYTER_URL` - URL Jupyter сервера
- `JUPYTER_TOKEN` - токен аутентификации для доступа к Jupyter серверу

### Опциональные
- `ALLOW_IMG_OUTPUT` - включение/выключение поддержки вывода изображений для мультимодальных возможностей
- `DOCUMENT_URL` - URL для хранения блокнотов (для продвинутых развертываний)
- `RUNTIME_URL` - URL для выполнения ядра (для продвинутых развертываний)
- `DOCUMENT_TOKEN` - токен для аутентификации в сервисе документов (для разных учетных данных)
- `RUNTIME_TOKEN` - токен для аутентификации в сервисе выполнения (для разных учетных данных)
- `DOCUMENT_ID` - путь к блокноту для подключения по умолчанию (относительно директории запуска JupyterLab)
- `JUPYTERHUB_ALLOW_TOKEN_IN_URL` - разрешить токен в URL для развертываний JupyterHub

## Ресурсы

- [GitHub Repository](https://github.com/datalayer/jupyter-mcp-server)

## Примечания

Совместим с любым развертыванием Jupyter (локальный, JupyterHub) и с хостинговыми блокнотами Datalayer. Требует определенных версий jupyterlab, jupyter-collaboration и datalayer_pycrdt для корректной работы функций совместной работы в реальном времени. Лучше всего использовать с мультимодальными LLM для полного использования возможностей. Пользователям JupyterHub необходимо установить JUPYTERHUB_ALLOW_TOKEN_IN_URL=1 и убедиться, что API токен имеет область доступа access:servers.