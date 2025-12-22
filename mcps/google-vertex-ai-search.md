---
title: Google Vertex AI Search MCP сервер
description: MCP сервер для поиска документов с использованием Vertex AI, который основывает ответы Gemini на ваших приватных данных, хранящихся в Vertex AI Datastore.
tags:
- AI
- Search
- Cloud
- Integration
- Analytics
author: ubie-oss
featured: false
---

MCP сервер для поиска документов с использованием Vertex AI, который основывает ответы Gemini на ваших приватных данных, хранящихся в Vertex AI Datastore.

## Установка

### Из исходного кода

```bash
git clone git@github.com:ubie-oss/mcp-vertexai-search.git
uv venv
uv sync --all-extras
uv run mcp-vertexai-search
```

### Python пакет

```bash
pip install git+https://github.com/ubie-oss/mcp-vertexai-search.git
```

## Возможности

- Интеграция с одним или несколькими хранилищами данных Vertex AI
- Использует Gemini с заземлением Vertex AI для улучшенного качества поиска
- Поддержка SSE (Server-Sent Events) и stdio транспортов
- Поддержка конфигурационных файлов YAML
- Автономное тестирование поиска без MCP сервера
- Поддержка олицетворения сервисного аккаунта

## Ресурсы

- [GitHub Repository](https://github.com/ubie-oss/mcp-vertexai-search)

## Примечания

Требует настройки хранилища данных Vertex AI и конфигурационного файла YAML на основе config.yml.template. Поддерживает как stdio, так и SSE транспорты. Может запускаться автономно для тестирования поиска или как MCP сервер.