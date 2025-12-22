---
title: Computer-Use - Remote MacOS Use MCP сервер
description: Первый open-source MCP сервер, который позволяет AI полностью управлять удалёнными macOS системами через демонстрацию экрана, предоставляя прямую альтернативу OpenAI Operator с полными возможностями рабочего стола.
tags:
- AI
- Productivity
- Integration
- Browser
- DevOps
author: Community
featured: false
---

Первый open-source MCP сервер, который позволяет AI полностью управлять удалёнными macOS системами через демонстрацию экрана, предоставляя прямую альтернативу OpenAI Operator с полными возможностями рабочего стола.

## Установка

### Docker

```bash
docker run -i -e MACOS_USERNAME=your_macos_username -e MACOS_PASSWORD=your_macos_password -e MACOS_HOST=your_macos_hostname_or_ip --rm buryhuang/mcp-remote-macos-use:latest
```

### Из исходного кода

```bash
git clone https://github.com/yourusername/mcp-remote-macos-use.git
cd mcp-remote-macos-use
docker build -t mcp-remote-macos-use .
```

### Кроссплатформенная публикация

```bash
docker buildx create --use
docker buildx build --platform linux/amd64,linux/arm64 -t buryhuang/mcp-remote-macos-use:latest --push .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "remote-macos-use": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "-e",
        "MACOS_USERNAME=your_macos_username",
        "-e",
        "MACOS_PASSWORD=your_macos_password",
        "-e",
        "MACOS_HOST=your_macos_hostname_or_ip",
        "--rm",
        "buryhuang/mcp-remote-macos-use:latest"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `remote_macos_get_screen` | Подключается к удалённой macOS машине и получает скриншот удалённого рабочего стола |
| `remote_macos_send_keys` | Отправляет клавиатурный ввод на удалённую macOS машину |
| `remote_macos_mouse_move` | Перемещает курсор мыши в указанные координаты на удалённой macOS машине с автоматической координатой... |
| `remote_macos_mouse_click` | Выполняет клик мыши в указанных координатах на удалённой macOS машине с автоматической координатой... |
| `remote_macos_mouse_double_click` | Выполняет двойной клик мыши в указанных координатах на удалённой macOS машине с автоматической к... |
| `remote_macos_mouse_scroll` | Выполняет прокрутку мыши в указанных координатах на удалённой macOS машине с автоматическими координ... |
| `remote_macos_open_application` | Открывает/активирует приложение и возвращает его PID для дальнейших взаимодействий |
| `remote_macos_mouse_drag_n_drop` | Выполняет операцию перетаскивания мыши от начальной точки до конечной точки на удалённой macOS машине, ... |

## Возможности

- Без дополнительных затрат на API: Бесплатная обработка экрана с вашим существующим планом Claude Pro
- Минимальная настройка: Просто включите Screen Sharing на целевом Mac – никакого дополнительного ПО не требуется
- Универсальная совместимость: Работает со всеми версиями macOS, текущими и будущими
- Универсальная совместимость с LLM: Работает с любым MCP клиентом на ваш выбор
- Гибкость моделей: Беспроблемная интеграция с OpenAI, Anthropic или любым другим провайдером LLM
- Нулевая настройка на целевых машинах: Не требуются фоновые приложения или агенты на macOS
- Поддержка WebRTC через LiveKit: Демонстрация экрана в реальном времени с низкой задержкой и улучшенной производительностью
- Автоматическая адаптация качества в зависимости от условий сети

## Переменные окружения

### Обязательные
- `MACOS_USERNAME` - Имя пользователя для удалённой macOS машины
- `MACOS_PASSWORD` - Пароль для удалённой macOS машины
- `MACOS_HOST` - Имя хоста или IP адрес удалённой macOS машины

## Примеры использования

```
Research Twitter and Post Twitter
```

```
Use CapCut to create short highlight video
```

```
AI Recruiter: Automated candidate information collection, qualifying applications and sending screening sessions using Mail App
```

```
AI Marketing Intern: LinkedIn engagement - automated following, liking, and commenting with relevant users
```

```
AI Marketing Intern: Twitter engagement - automated following, liking, and commenting with relevant users
```

## Ресурсы

- [GitHub Repository](https://github.com/baryhuang/mcp-remote-macos-use)

## Примечания

Требуется включение Screen Sharing на целевой macOS машине. Поддерживает только Apple Authentication (протокол 30). Использует протокол согласования ключей Diffie-Hellman с 512-битным простым числом для безопасности. Поддержка WebRTC требует настройки LiveKit сервера для улучшенной производительности.