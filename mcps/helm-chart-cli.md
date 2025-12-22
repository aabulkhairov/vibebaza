---
title: Helm Chart CLI MCP сервер
description: Helm MCP предоставляет связующее звено между AI-ассистентами и пакетным менеджером Helm для Kubernetes, позволяя взаимодействовать с Helm на естественном языке для установки чартов, управления репозиториями и многого другого.
tags:
- DevOps
- Cloud
- Integration
- API
author: Community
featured: false
---

Helm MCP предоставляет связующее звено между AI-ассистентами и пакетным менеджером Helm для Kubernetes, позволяя взаимодействовать с Helm на естественном языке для установки чартов, управления репозиториями и многого другого.

## Установка

### Docker

```bash
# Clone the repository
git clone https://github.com/modelcontextprotocol/servers.git
cd src/helm

# Build the Docker image
docker build -t mcp-helm .
```

### Ручная установка

```bash
# Clone the repository
git clone https://github.com/modelcontextprotocol/servers.git
cd src/helm

# Install dependencies
uv venv
source .venv/Scripts/Activate.ps1
uv pip install -e .

# Run the server
mcp-server-helm
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `helm_completion` | Генерирует скрипты автодополнения для различных оболочек |
| `helm_create` | Создает новый чарт с указанным именем |
| `helm_lint` | Запускает серию тестов для проверки корректности чарта |
| `helm_package` | Упаковывает чарт в архив |
| `helm_template` | Рендерит шаблоны чарта локально и отображает результат |
| `helm_dependency_build` | Собирает зависимости чарта |
| `helm_dependency_list` | Выводит список зависимостей для указанного чарта |
| `helm_dependency_update` | Обновляет зависимости чарта |
| `helm_env` | Показывает информацию о среде Helm |
| `helm_version` | Показывает информацию о версии Helm |
| `helm_install` | Устанавливает чарт |
| `helm_uninstall` | Удаляет релиз |
| `helm_upgrade` | Обновляет релиз |
| `helm_rollback` | Откатывает релиз к предыдущей ревизии |
| `helm_list` | Выводит список релизов |

## Возможности

- Создание и управление чартами
- Управление зависимостями
- Установка и управление релизами
- Управление репозиториями
- Операции с реестром
- Получение информации о чартах
- Управление плагинами
- Информация о среде и версии
- Взаимодействие с командами Helm на естественном языке
- Генерация скриптов автодополнения

## Ресурсы

- [GitHub Repository](https://github.com/jeff-nasseri/helm-chart-cli-mcp)

## Примечания

Предварительные требования: Python 3.8+, Docker (для контейнеризованного деплоя), установленный Helm CLI. Включает значки оценки безопасности от MseeP.ai.