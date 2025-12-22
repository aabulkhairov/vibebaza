---
title: Jenkins MCP сервер
description: MCP сервер, который позволяет создавать и управлять задачами сборки Jenkins через Model Context Protocol.
tags:
- DevOps
- Integration
- Code
- Productivity
- API
author: jasonkylelol
featured: false
---

MCP сервер, который позволяет создавать и управлять задачами сборки Jenkins через Model Context Protocol.

## Установка

### Из исходного кода

```bash
python3 mcp_server.py
```

## Возможности

- Создание задач сборки Jenkins
- Мониторинг выполнения задач сборки
- Получение результатов сборки при завершении задач

## Переменные окружения

### Обязательные
- `JENKINS_URL` - URL сервера Jenkins
- `JENKINS_USER` - имя пользователя Jenkins
- `JENKINS_TOKEN` - токен API Jenkins
- `OPENAI_API_BASE_URL` - базовый URL API OpenAI
- `OPENAI_MODEL` - модель OpenAI для использования
- `OPENAI_API_KEY` - ключ API OpenAI

## Ресурсы

- [GitHub Repository](https://github.com/jasonkylelol/jenkins-mcp-server)

## Примечания

Требует редактирования файла .env с учетными данными Jenkins и конфигурацией OpenAI. Также требует изменения server_config.json для конфигурации порта MCP сервера. Используйте python3 mcp_client.py для тестирования задач сборки Jenkins.