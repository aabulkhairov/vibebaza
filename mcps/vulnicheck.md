---
title: vulnicheck MCP сервер
description: ИИ-powered сканер безопасности, который обеспечивает комплексное обнаружение уязвимостей для Python проектов и GitHub репозиториев, используя множественные базы данных уязвимостей и улучшенную ИИ-оценку рисков.
tags:
- Security
- DevOps
- AI
- Code
- Analytics
author: Community
featured: false
install_command: claude mcp add --transport http vulnicheck http://localhost:3000/mcp
---

ИИ-powered сканер безопасности, который обеспечивает комплексное обнаружение уязвимостей для Python проектов и GitHub репозиториев, используя множественные базы данных уязвимостей и улучшенную ИИ-оценку рисков.

## Установка

### Docker

```bash
# Pull the latest image from Docker Hub
docker pull andrasfe/vulnicheck:latest

# Run with OpenAI API key (for enhanced AI-powered risk assessment)
docker run -d --name vulnicheck-mcp -p 3000:3000 \
  --restart=unless-stopped \
  -e OPENAI_API_KEY=your-openai-api-key \
  andrasfe/vulnicheck:latest

# Or run without API key (basic vulnerability scanning)
docker run -d --name vulnicheck-mcp -p 3000:3000 \
  --restart=unless-stopped \
  andrasfe/vulnicheck:latest
```

### Из исходников

```bash
# Clone the repository
git clone https://github.com/andrasfe/vulnicheck.git
cd vulnicheck

# Build Docker image
docker build -t vulnicheck .

# Run locally built image (no auth)
docker run -d --name vulnicheck-mcp -p 3000:3000 --restart=unless-stopped vulnicheck
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `check_package_vulnerabilities` | Проверить конкретный Python пакет на уязвимости |
| `scan_dependencies` | Сканировать файлы зависимостей (requirements.txt, pyproject.toml, и т.д.) |
| `scan_installed_packages` | Сканировать установленные в данный момент Python пакеты |
| `get_cve_details` | Получить подробную информацию о конкретной CVE |
| `scan_for_secrets` | Обнаруживать скрытые секреты и учетные данные в коде |
| `scan_dockerfile` | Анализировать Dockerfiles на предмет уязвимых Python зависимостей |
| `scan_github_repo` | Комплексное сканирование безопасности GitHub репозиториев |
| `assess_operation_safety` | ИИ-powered оценка рисков для операций |
| `validate_mcp_security` | Валидировать конфигурации безопасности MCP сервера |
| `comprehensive_security_check` | Интерактивная ИИ-powered оценка безопасности |

## Возможности

- Docker деплой: Безопасный контейнеризированный деплой с HTTP стримингом (не требует SSE/Server-Sent Events)
- Опциональная аутентификация: Поддерживает Google OAuth 2.0 для безопасного контроля доступа (по умолчанию отключено)
- Готовность к продакшену: Масштабируемая архитектура HTTP сервера
- Комплексное покрытие: Опрашивает 5+ баз данных уязвимостей (OSV.dev, NVD, GitHub Advisory, CIRCL, Safety DB)
- Интеграция с GitHub: Сканирование любого публичного/приватного GitHub репозитория напрямую (до 1GB)
- ИИ-powered анализ: Использует OpenAI/Anthropic API для интеллектуальной оценки безопасности
- Обнаружение секретов: Находит открытые API ключи, пароли и учетные данные
- Безопасность Docker: Анализирует Dockerfiles на предмет уязвимых зависимостей
- Умное кеширование: Избегает избыточных сканирований с кешированием на уровне коммитов
- Управление местом: Автоматическая очистка предотвращает исчерпание диска (лимит 2GB)

## Переменные окружения

### Опциональные
- `OPENAI_API_KEY` - ИИ-powered оценка рисков
- `ANTHROPIC_API_KEY` - Альтернативный ИИ провайдер
- `GITHUB_TOKEN` - Более высокие лимиты GitHub API
- `NVD_API_KEY` - Более высокие лимиты NVD
- `FASTMCP_SERVER_AUTH_GOOGLE_CLIENT_ID` - Google OAuth client ID для аутентификации
- `FASTMCP_SERVER_AUTH_GOOGLE_CLIENT_SECRET` - Google OAuth client secret для аутентификации
- `FASTMCP_SERVER_BASE_URL` - Базовый URL для OAuth callbacks

## Примеры использования

```
Run a comprehensive security check on my project
```

```
Scan https://github.com/owner/repo for vulnerabilities
```

```
Check my dependencies for security issues
```

```
Scan my Dockerfile for vulnerable packages
```

## Ресурсы

- [GitHub Repository](https://github.com/andrasfe/vulnicheck)

## Примечания

OAuth аутентификация в настоящее время имеет известные ограничения с HTTP транспортом из-за проблем FastMCP 2.12.4. Для внешних клиентов запускайте без аутентификации. Поддерживает requirements.txt, pyproject.toml, setup.py, Dockerfiles, и все текстовые файлы исходников. Официальный Docker образ доступен как andrasfe/vulnicheck на Docker Hub.