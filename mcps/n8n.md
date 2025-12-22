---
title: n8n MCP сервер
description: MCP сервер, который позволяет AI ассистентам взаимодействовать с n8n воркфлоу через естественный язык, обеспечивая программное управление и контроль n8n воркфлоу и их выполнением.
tags:
- Integration
- DevOps
- Productivity
- API
author: Community
featured: false
---

MCP сервер, который позволяет AI ассистентам взаимодействовать с n8n воркфлоу через естественный язык, обеспечивая программное управление и контроль n8n воркфлоу и их выполнением.

## Установка

### NPM Global

```bash
npm install -g @leonardsellem/n8n-mcp-server
```

### Из исходного кода

```bash
git clone https://github.com/leonardsellem/n8n-mcp-server.git
cd n8n-mcp-server
npm install
npm run build
npm install -g .
```

### Docker

```bash
docker pull leonardsellem/n8n-mcp-server
docker run -e N8N_API_URL=http://your-n8n:5678/api/v1 \
  -e N8N_API_KEY=your_n8n_api_key \
  -e N8N_WEBHOOK_USERNAME=username \
  -e N8N_WEBHOOK_PASSWORD=password \
  leonardsellem/n8n-mcp-server
```

## Конфигурация

### Конфигурация AI ассистента

```json
{
  "mcpServers": {
    "n8n-local": {
      "command": "node",
      "args": [
        "/path/to/your/cloned/n8n-mcp-server/build/index.js"
      ],
      "env": {
        "N8N_API_URL": "http://your-n8n-instance:5678/api/v1",
        "N8N_API_KEY": "YOUR_N8N_API_KEY",
        "N8N_WEBHOOK_USERNAME": "your_webhook_user",
        "N8N_WEBHOOK_PASSWORD": "your_webhook_password"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `workflow_list` | Получить список всех воркфлоу |
| `workflow_get` | Получить детали конкретного воркфлоу |
| `workflow_create` | Создать новый воркфлоу |
| `workflow_update` | Обновить существующий воркфлоу |
| `workflow_delete` | Удалить воркфлоу |
| `workflow_activate` | Активировать воркфлоу |
| `workflow_deactivate` | Деактивировать воркфлоу |
| `execution_run` | Выполнить воркфлоу через API |
| `run_webhook` | Выполнить воркфлоу через webhook |
| `execution_get` | Получить детали конкретного выполнения |
| `execution_list` | Получить список выполнений воркфлоу |
| `execution_stop` | Остановить выполняющийся воркфлоу |

## Возможности

- Мост между AI ассистентами и инструментом автоматизации воркфлоу n8n
- Полное управление воркфлоу (создание, чтение, обновление, удаление, активация/деактивация)
- Мониторинг и контроль выполнения
- Запуск воркфлоу через webhook с Basic аутентификацией
- Доступ к ресурсам воркфлоу и их выполнений
- Поддержка Docker для контейнерного деплоя
- Возможности отладочного логирования

## Переменные окружения

### Обязательные
- `N8N_API_URL` - Полный URL n8n API, включая /api/v1
- `N8N_API_KEY` - API ключ для аутентификации с n8n

### Опциональные
- `N8N_WEBHOOK_USERNAME` - Имя пользователя для аутентификации webhook (если используются webhook)
- `N8N_WEBHOOK_PASSWORD` - Пароль для аутентификации webhook
- `DEBUG` - Включить отладочное логирование (опционально)

## Примеры использования

```
Выполнить воркфлоу через webhook с данными: run_webhook с workflowName 'hello-world' и данными, содержащими prompt 'Hello from AI assistant!'
```

## Ресурсы

- [GitHub Repository](https://github.com/leonardsellem/n8n-mcp-server)

## Примечания

Требует Node.js 20 или новее и экземпляр n8n с включенным доступом к API. API ключ можно сгенерировать в n8n Settings > API > API Keys. Сервер предоставляет ресурсы для воркфлоу и их выполнений с URI типа n8n://workflows/list и n8n://workflow/{id}. Проект, развиваемый сообществом, ищет со-мейнтейнеров.