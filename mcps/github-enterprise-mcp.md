---
title: GitHub Enterprise MCP сервер
description: MCP сервер для интеграции с GitHub Enterprise API, предоставляющий доступ к информации о репозиториях, issues, PR, workflows и управлению пользователями из экземпляров GitHub Enterprise.
tags:
- DevOps
- API
- Code
- Integration
- Productivity
author: ddukbg
featured: false
---

MCP сервер для интеграции с GitHub Enterprise API, предоставляющий доступ к информации о репозиториях, issues, PR, workflows и управлению пользователями из экземпляров GitHub Enterprise.

## Установка

### Docker

```bash
docker build -t github-enterprise-mcp .
docker run -p 3000:3000 \
  -e GITHUB_TOKEN="your_github_token" \
  -e GITHUB_ENTERPRISE_URL="https://github.your-company.com/api/v3" \
  -e DEBUG=true \
  github-enterprise-mcp
```

### Docker Compose

```bash
# Create .env file with required variables
docker-compose up -d
```

### Из исходного кода (разработка)

```bash
git clone https://github.com/ddukbg/github-enterprise-mcp.git
cd github-enterprise-mcp
npm install
export GITHUB_TOKEN="your_github_token"
export GITHUB_ENTERPRISE_URL="https://github.your-company.com/api/v3"
npm run dev
```

### Из исходного кода (продакшн)

```bash
git clone https://github.com/ddukbg/github-enterprise-mcp.git
cd github-enterprise-mcp
npm install
npm run build
chmod +x dist/index.js
export GITHUB_TOKEN="your_github_token"
export GITHUB_ENTERPRISE_URL="https://github.your-company.com/api/v3"
node dist/index.js --transport http --debug
```

### Глобальная установка

```bash
npm link
export GITHUB_TOKEN="your_github_token"
export GITHUB_ENTERPRISE_URL="https://github.your-company.com/api/v3"
github-enterprise-mcp --transport=http --debug
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "github-enterprise": {
      "command": "npx",
      "args": ["-y", "@ddukbg/github-enterprise-mcp", "--token=YOUR_GITHUB_TOKEN", "--github-enterprise-url=YOUR_GITHUB_ENTERPRISE_URL"]
    }
  }
}
```

### Cursor (URL режим)

```json
{
  "mcpServers": {
    "github-enterprise": {
      "url": "http://localhost:3000/sse"
    }
  }
}
```

### Cursor (режим команд)

```json
{
  "mcpServers": {
    "github-enterprise": {
      "command": "npx",
      "args": [
        "@ddukbg/github-enterprise-mcp"
      ],
      "env": {
        "GITHUB_ENTERPRISE_URL": "https://github.your-company.com/api/v3",
        "GITHUB_TOKEN": "your_github_token"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list-repositories` | Получить список репозиториев для пользователя или организации |
| `get-repository` | Получить детальную информацию о репозитории |
| `list-branches` | Список веток репозитория |
| `get-content` | Получить содержимое файла или директории |
| `list-pull-requests` | Список pull request'ов в репозитории |
| `get-pull-request` | Получить детали pull request'а |
| `create-pull-request` | Создать новый pull request |
| `merge-pull-request` | Выполнить merge pull request'а |
| `list-issues` | Список issues в репозитории |
| `get-issue` | Получить детали issue |
| `list-issue-comments` | Список комментариев к issue или pull request'у |
| `create-issue` | Создать новый issue |
| `create-repository` | Создать новый репозиторий |
| `update-repository` | Обновить настройки репозитория |
| `delete-repository` | Удалить репозиторий |

## Возможности

- Получение списка репозиториев из экземпляров GitHub Enterprise
- Получение детальной информации о репозиториях
- Просмотр веток репозитория
- Просмотр содержимого файлов и директорий
- Управление issues и pull request'ами
- Управление репозиториями (создание, обновление, удаление)
- Управление workflow'ами GitHub Actions
- Управление пользователями (список, создание, обновление, удаление, блокировка/разблокировка пользователей)
- Доступ к статистике предприятия
- Улучшенная обработка ошибок и дружелюбное форматирование ответов

## Переменные окружения

### Обязательные
- `GITHUB_TOKEN` - GitHub Personal Access Token для аутентификации
- `GITHUB_ENTERPRISE_URL` - URL GitHub Enterprise API (например, https://github.your-company.com/api/v3)

### Опциональные
- `DEBUG` - Включить debug логирование
- `LANGUAGE` - Установить язык (en или ko, по умолчанию: en)

## Примеры использования

```
Список репозиториев для пользователя: mcp_github_enterprise_list_repositories(owner="octocat")
```

```
Получить информацию о репозитории: mcp_github_enterprise_get_repository(owner="octocat", repo="hello-world")
```

```
Список открытых pull request'ов: mcp_github_enterprise_list_pull_requests(owner="octocat", repo="hello-world", state="open")
```

```
Создать новый issue: mcp_github_enterprise_create_issue(owner="octocat", repo="hello-world", title="Found a bug", body="Description", labels=["bug"])
```

```
Получить содержимое файла: mcp_github_enterprise_get_content(owner="octocat", repo="hello-world", path="README.md")
```

## Ресурсы

- [GitHub Repository](https://github.com/ddukbg/github-enterprise-mcp)

## Примечания

Требует Node.js 18 или выше. Некоторые специфичные для предприятия функции (информация о лицензиях и статистика предприятия) требуют привилегий администратора сайта и не будут работать с GitHub.com или GitHub Enterprise Cloud. URL режим рекомендуется для интеграции с Cursor, так как он более стабилен, чем режим команд.