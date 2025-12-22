---
title: libvirt-mcp MCP сервер
description: Экспериментальный MCP сервер для libvirt, который позволяет LLM взаимодействовать с libvirt для создания, удаления или получения списка виртуальных машин в системе.
tags:
- DevOps
- Cloud
- Integration
author: Community
featured: false
---

Экспериментальный MCP сервер для libvirt, который позволяет LLM взаимодействовать с libvirt для создания, удаления или получения списка виртуальных машин в системе.

## Установка

### Из исходного кода с зависимостями

```bash
# Install mcp-cli
git clone https://github.com/chrishayuk/mcp-cli
pip3.11 install -e ".[cli,dev]"

# Install ollama
curl -fsSL https://ollama.com/install.sh | sh
ollama serve >/dev/null 2>&1 &
ollama pull granite3.2:8b-instruct-q8_0

# Install uv
pip install uv

# Install python bindings
dnf install -y libvirt-devel python3-devel

# In libvirt-mcp directory
uv sync
```

## Возможности

- Создание виртуальных машин через libvirt
- Удаление виртуальных машин через libvirt
- Получение списка виртуальных машин в системе
- Интеграция с ollama и моделями granite
- Совместимость с mcp-cli

## Ресурсы

- [GitHub Repository](https://github.com/MatiasVara/libvirt-mcp)

## Примечания

Требует редактирования server_config.json для установки правильного пути к libvirt-mcp серверу. Запуск осуществляется через скрипт run.sh, который использует ollama как провайдер и granite как модель. Для отладки установите mcp через npm и выполните 'mcp dev setup.py'. Включает демо GIF с интеграцией Claude.