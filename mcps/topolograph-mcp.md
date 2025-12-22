---
title: Topolograph MCP сервер
description: MCP сервер, который предоставляет доступ к Topolograph API для анализа сетевых топологий OSPF/IS-IS, мониторинга событий и расчета маршрутов.
tags:
- Monitoring
- Analytics
- API
- DevOps
- Integration
author: Vadims06
featured: false
---

MCP сервер, который предоставляет доступ к Topolograph API для анализа сетевых топологий OSPF/IS-IS, мониторинга событий и расчета маршрутов.

## Установка

### Из исходного кода

```bash
pip install -r requirements.txt
```

### Docker Compose

```bash
git clone https://github.com/Vadims06/topolograph-docker.git
cd topolograph-docker
docker-compose pull
docker-compose up -d
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_all_graphs` | Список доступных графов с опциями фильтрации |
| `get_graph_by_time` | Получение конкретного графа по времени |
| `get_network_by_graph_time` | Запрос информации о сети |
| `get_graph_status` | Проверка здоровья графа и связности |
| `get_network_events` | Получение событий включения/выключения сети |
| `get_adjacency_events` | Получение событий узлов/хостов и связей |
| `get_nodes` | Запрос узлов диаграммы |
| `get_edges` | Запрос рёбер диаграммы |
| `get_shortest_path` | Расчет кратчайших путей между узлами |
| `upload_graph` | Загрузка новых графов в API |

## Возможности

- Управление графами: Получение и загрузка сетевых графов
- Анализ сети: Запросы информации о сети по IP, ID узла или сетевой маске
- Мониторинг событий: Отслеживание сетевых событий и событий смежности с фильтрацией по времени
- Расчет маршрутов: Вычисление кратчайших путей между узлами с поддержкой резервных путей
- Мониторинг статуса: Проверка связности и здоровья графов
- Запросы узлов/рёбер: Получение детальной информации об узлах и рёбрах из диаграмм

## Переменные окружения

### Обязательные
- `TOPOLOGRAPH_API_BASE` - Базовый URL для Topolograph API

### Опциональные
- `TOPOLOGRAPH_API_TOKEN` - API токен для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/Vadims06/topolograph-mcp-server)

## Примечания

Сервер работает по умолчанию на http://0.0.0.0:8000/mcp и включен в репозиторий topolograph-docker для удобного деплоя. При использовании Docker Compose он доступен по адресу http://localhost:8000/mcp и автоматически подключается к Flask API.