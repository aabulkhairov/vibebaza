---
title: ShaderToy MCP сервер
description: MCP сервер для ShaderToy, который связывает LLM с сайтом ShaderToy,
  позволяя им запрашивать и читать информацию о шейдерах для создания сложных GLSL шейдеров,
  которые они обычно не способны создать самостоятельно.
tags:
- API
- Web Scraping
- Code
- Media
- AI
author: wilsonchenghy
featured: false
---

MCP сервер для ShaderToy, который связывает LLM с сайтом ShaderToy, позволяя им запрашивать и читать информацию о шейдерах для создания сложных GLSL шейдеров, которые они обычно не способны создать самостоятельно.

## Установка

### UV (Mac)

```bash
brew install uv
```

### UV (Windows)

```bash
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
set Path=C:\Users\nntra\.local\bin;%Path%
```

### Из исходников

```bash
git clone https://github.com/wilsonchenghy/ShaderToy-MCP.git
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "ShaderToy_MCP": {
          "command": "uv",
          "args": [
            "run",
            "--with",
            "mcp[cli]",
            "mcp",
            "run",
            "<path_to_project>/ShaderToy-MCP/src/ShaderToy-MCP/server.py"
          ],
          "env": {
            "SHADERTOY_APP_KEY": "your_actual_api_key"  // Replace with your API key
          }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_shader_info` | Получает информацию о любом шейдере на ShaderToy |
| `search_shader` | Ищет шейдеры, доступные на ShaderToy, по поисковому запросу |

## Возможности

- Получение информации о любом шейдере на ShaderToy
- Поиск шейдеров, доступных на ShaderToy, по поисковому запросу
- Генерация сложных шейдеров путем изучения существующих шейдеров на ShaderToy

## Переменные окружения

### Обязательные
- `SHADERTOY_APP_KEY` - API ключ для доступа к ShaderToy

## Примеры использования

```
Generate shader code of a {object}, if it is based on someone's work on ShaderToy, credit it, make the code follow the ShaderToy format: void mainImage( out vec4 fragColor, in vec2 fragCoord ) {}
```

## Ресурсы

- [GitHub Repository](https://github.com/wilsonchenghy/ShaderToy-MCP)

## Примечания

Сервер позволяет LLM создавать сложные шейдеры, такие как океан, горы и эффекты цифрового дождя из Матрицы, изучая существующие примеры на ShaderToy.