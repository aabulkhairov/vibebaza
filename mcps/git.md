---
title: Git MCP сервер
description: Model Context Protocol (MCP) сервер для взаимодействия с Git репозиториями
  и автоматизации, написанный на Go. Этот сервер предоставляет инструменты для чтения, поиска и
  манипулирования Git репозиториями через большие языковые модели.
tags:
- DevOps
- Code
- Productivity
author: geropl
featured: false
---

Model Context Protocol (MCP) сервер для взаимодействия с Git репозиториями и автоматизации, написанный на Go. Этот сервер предоставляет инструменты для чтения, поиска и манипулирования Git репозиториями через большие языковые модели.

## Установка

### Готовые бинарные файлы

```bash
Download prebuilt binaries from the GitHub Releases page: https://github.com/geropl/git-mcp-go/releases
```

### Go Install

```bash
go install github.com/geropl/git-mcp-go@latest
```

### Из исходного кода

```bash
git clone https://github.com/geropl/git-mcp-go.git
cd git-mcp-go
go build -o git-mcp-go .
```

### Автоматическая установка (Linux)

```bash
RELEASE="$(curl -s https://api.github.com/repos/geropl/git-mcp-go/releases/latest)"
DOWNLOAD_URL="$(echo $RELEASE | jq -r '.assets[] | select(.name | contains("linux-amd64")) | .browser_download_url')"
curl -L -o ./git-mcp-go $DOWNLOAD_URL
chmod +x ./git-mcp-go
./git-mcp-go setup -r /path/to/git/repository --tool=cline --auto-approve=allow-local-only
rm -f ./git-mcp-go
```

## Конфигурация

### Claude Desktop (Несколько репозиториев)

```json
{
  "mcpServers": {
    "git": {
      "command": "/path/to/git-mcp-go",
      "args": ["serve", "-r=/path/to/repo1,/path/to/repo2", "--mode", "shell"]
    }
  }
}
```

### Claude Desktop (Один репозиторий)

```json
{
  "mcpServers": {
    "git": {
      "command": "/path/to/git-mcp-go",
      "args": ["serve", "-r", "/path/to/git/repository"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `git_status` | Показывает статус рабочего дерева |
| `git_diff_unstaged` | Показывает изменения в рабочем каталоге, которые еще не добавлены в индекс |
| `git_diff_staged` | Показывает изменения, которые добавлены в индекс для коммита |
| `git_diff` | Показывает различия между ветками или коммитами |
| `git_commit` | Записывает изменения в репозиторий |
| `git_add` | Добавляет содержимое файлов в область индексации |
| `git_reset` | Убирает все изменения из индекса |
| `git_log` | Показывает журнал коммитов |
| `git_create_branch` | Создает новую ветку из опциональной базовой ветки |
| `git_checkout` | Переключает ветки |
| `git_show` | Показывает содержимое коммита |
| `git_init` | Инициализирует новый Git репозиторий |
| `git_push` | Отправляет локальные коммиты в удаленный репозиторий (требует флаг --write-access) |
| `git_list_repositories` | Показывает список всех доступных Git репозиториев |

## Возможности

- Поддержка нескольких репозиториев - мониторинг и работа с несколькими репозиториями одновременно
- Два режима реализации: shell (Git CLI) и go-git (чистая Go реализация)
- Контроль доступа на запись с опциональным флагом --write-access для удаленных операций
- Опции автоподтверждения для выполнения инструментов (allow-read-only, allow-local-only или конкретные инструменты)
- Команда автоматической настройки для легкой интеграции с AI ассистентами
- Комплексные Git операции, включая индексацию, коммиты, ветвление и удаленные операции
- Управление репозиториями с возможностью просмотра списка и выбора

## Ресурсы

- [GitHub Repository](https://github.com/geropl/git-mcp-go)

## Примечания

Сервер поддерживает как операции через shell-based Git CLI, так и чистую Go реализацию через библиотеку go-git. Доступ на запись по умолчанию отключен для безопасности и должен быть явно включен флагом --write-access. Команда setup обеспечивает автоматическую установку и конфигурацию для AI ассистентов, таких как Cline.