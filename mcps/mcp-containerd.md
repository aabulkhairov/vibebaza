---
title: mcp-containerd MCP сервер
description: MCP сервер, реализованный на Rust с использованием библиотеки RMCP для управления Containerd, поддерживающий все операции CRI интерфейса включая runtime и image сервисы.
tags:
- DevOps
- Code
- Cloud
- Integration
- Monitoring
author: jokemanfire
featured: false
---

MCP сервер, реализованный на Rust с использованием библиотеки RMCP для управления Containerd, поддерживающий все операции CRI интерфейса включая runtime и image сервисы.

## Установка

### Из исходного кода

```bash
cargo build --release
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_containers` | Выводит список всех контейнеров в containerd |
| `list_images` | Выводит список всех образов в containerd |
| `version` | Предоставляет информацию о версии CRI |
| `create_pod_sandbox` | Создает Pod sandbox |
| `stop_pod_sandbox` | Останавливает Pod sandbox |
| `delete_pod_sandbox` | Удаляет Pod sandbox |
| `create_container` | Создает контейнер |
| `start_container` | Запускает контейнер |
| `stop_container` | Останавливает контейнер |
| `delete_container` | Удаляет контейнер |
| `get_image_status` | Получает статус образа |
| `pull_images` | Загружает образы контейнеров |
| `delete_images` | Удаляет образы контейнеров |
| `get_image_filesystem_info` | Получает информацию о файловой системе образа |

## Возможности

- Реализует MCP сервер с использованием библиотеки RMCP
- Поддерживает все операции Containerd CRI интерфейса
- Предоставляет интерфейсы Runtime Service
- Предоставляет интерфейсы Image Service
- Поддерживает ctr интерфейс
- Операции создания/остановки/удаления Pod Sandbox
- Операции создания/запуска/остановки/удаления контейнеров
- Запрос статуса Pod/контейнеров
- Выполнение команд в контейнерах
- Список, загрузка и удаление образов

## Примеры использования

```
please give me a list of containers
```

```
please give me a list of images
```

## Ресурсы

- [GitHub Repository](https://github.com/jokemanfire/mcp-containerd)

## Примечания

Требует среду разработки Rust, установленный и запущенный Containerd, а также инструменты компиляции Protobuf. По умолчанию подключается к эндпоинту unix:///run/containerd/containerd.sock. Может быть запущен с 'mcp-containerd -t http' для stream HTTP или 'mcp-containerd --help' для получения справочной информации.