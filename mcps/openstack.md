---
title: OpenStack MCP сервер
description: Сервис запросов ресурсов OpenStack на основе MCP, который предоставляет API интерфейсы для запроса вычислительных ресурсов, хранилища, сети, образов и других ресурсов из облачных платформ OpenStack.
tags:
- Cloud
- DevOps
- API
- Monitoring
- Integration
author: wangsqly0407
featured: false
---

Сервис запросов ресурсов OpenStack на основе MCP, который предоставляет API интерфейсы для запроса вычислительных ресурсов, хранилища, сети, образов и других ресурсов из облачных платформ OpenStack.

## Установка

### pip

```bash
pip install openstack-mcp-server
```

### Из исходного кода

```bash
git clone https://github.com/wangshqly0407/openstack-mcp-server.git
cd openstack-mcp-server
uv venv
source .venv/bin/activate
uv sync
uv run ./src/mcp_openstack_http/server.py --port 8000 --log-level INFO --auth-url 'http://<OpenStack-API-Endpoint>:5000/v3' --username '<OpenStack-Admin-User>' --password '<OpenStack-Admin-Password>'
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_instances` | Получение VM инстансов OpenStack с фильтрацией и контролем уровня детализации |

## Возможности

- Запросы ресурсов в реальном времени: получение актуального статуса ресурсов кластеров OpenStack через API
- Многомерная информация: поддержка запросов различных ресурсов, включая вычислительные мощности, хранилище, сеть и образы
- Гибкая фильтрация: фильтрация ресурсов по имени, ID и другим условиям
- Контроль уровня детализации: поддержка базового, детального и полного уровней отображения информации
- Стандартный MCP интерфейс: полная совместимость с протоколом MCP, бесшовная интеграция с большими языковыми моделями
- Высокопроизводительный асинхронный HTTP сервис на основе Starlette и Uvicorn
- SSE потоковый вывод для обратной связи в реальном времени

## Примеры использования

```
Get OpenStack VM instances with filter 'web-server' and detailed information
```

## Ресурсы

- [GitHub Repository](https://github.com/wangsqly0407/openstack-mcp-server)

## Примечания

Требует Python 3.10+ и окружение OpenStack. Сервис по умолчанию запускается на порту 8000 с MCP интерфейсом, доступным по адресу http://localhost:8000/openstack. Поддерживает параметры командной строки для конфигурации порта, уровня логирования, auth URL, имени пользователя и пароля.