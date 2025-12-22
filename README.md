# VibeBaza Library

Open-source библиотека промптов, навыков, агентов и MCP-серверов для Claude Code.

**[vibebaza.com](https://vibebaza.com)** — сайт с поиском и каталогом всего контента.

## Что внутри

| Папка | Описание | Кол-во |
|-------|----------|--------|
| `skills/` | Навыки и экспертизы для Claude | 500+ |
| `agents/` | Готовые агенты с инструментами | 120+ |
| `prompts/` | Системные промпты | 35+ |
| `mcps/` | MCP-серверы (Model Context Protocol) | 850+ |
| `bundles/` | Связки (комбинации контента) | 14 |

---

## Быстрый старт

### 1. Fork и Clone

```bash
# Форкни репозиторий на GitHub, затем:
git clone git@github.com:YOUR_USERNAME/vibebaza.git
cd vibebaza
```

### 2. Создай файл

```bash
# Пример: новый скилл
touch skills/my-awesome-skill.md
```

### 3. Добавь контент

Открой файл и заполни по шаблону (примеры ниже).

### 4. Отправь PR

```bash
git add .
git commit -m "Add my-awesome-skill"
git push origin main
# Открой Pull Request на GitHub
```

---

## Полные примеры файлов

### Skill (Навык)

**Файл:** `skills/python-fastapi-expert.md`

```markdown
---
title: "FastAPI Backend Expert"
description: "Экспертиза в разработке REST API на Python с FastAPI, Pydantic, SQLAlchemy"
tags:
  - python
  - fastapi
  - backend
  - api
author: "VibeCoder"
featured: true
---

You are an expert Python backend developer specializing in FastAPI framework.

## Core Expertise

- FastAPI application architecture
- Pydantic models and validation
- SQLAlchemy ORM with async support
- OAuth2 and JWT authentication
- OpenAPI documentation

## Code Style

- Type hints everywhere
- Dependency injection pattern
- Repository pattern for data access
- Async/await for I/O operations

## Example Response

When asked to create an endpoint:

\`\`\`python
from fastapi import APIRouter, Depends, HTTPException
from sqlalchemy.ext.asyncio import AsyncSession

router = APIRouter(prefix="/users", tags=["users"])

@router.get("/{user_id}", response_model=UserResponse)
async def get_user(
    user_id: int,
    db: AsyncSession = Depends(get_db)
) -> UserResponse:
    user = await user_repo.get_by_id(db, user_id)
    if not user:
        raise HTTPException(404, "User not found")
    return user
\`\`\`
```

---

### Agent (Агент)

**Файл:** `agents/code-reviewer.md`

```markdown
---
title: "Code Reviewer Agent"
description: "Автоматический ревью кода с проверкой безопасности, стиля и производительности"
tags:
  - code-review
  - security
  - best-practices
author: "VibeCoder"
featured: false
agent_name: "code-reviewer"
agent_tools: "Read, Glob, Grep, Bash"
agent_model: "sonnet"
---

You are a senior code reviewer agent. Your job is to review code changes and provide actionable feedback.

## Review Checklist

1. **Security** — SQL injection, XSS, secrets in code
2. **Performance** — N+1 queries, unnecessary loops
3. **Readability** — naming, comments, complexity
4. **Tests** — coverage, edge cases

## Output Format

For each issue found:

\`\`\`
## [SEVERITY] Issue Title

**File:** path/to/file.py:42
**Type:** Security | Performance | Style | Bug

**Problem:**
Description of the issue.

**Suggestion:**
How to fix it with code example.
\`\`\`

## Tools Usage

- Use `Glob` to find relevant files
- Use `Read` to examine file contents
- Use `Grep` to search for patterns
- Use `Bash` only for git diff commands
```

---

### MCP Server

**Файл:** `mcps/notion.md`

```markdown
---
title: "Notion MCP Server"
description: "Интеграция с Notion API для работы со страницами, базами данных и блоками"
tags:
  - notion
  - productivity
  - database
  - official
author: "Anthropic"
featured: true
install_command: "npx -y @anthropic/mcp-notion"
connection_type: "stdio"
paid_api: false
---

Official MCP server for Notion integration.

## Features

- Read and write Notion pages
- Query databases
- Create and update blocks
- Search across workspace

## Setup

1. Get your Notion API key from [notion.so/my-integrations](https://notion.so/my-integrations)
2. Add the integration to your workspace

## Configuration

\`\`\`json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-notion"],
      "env": {
        "NOTION_API_KEY": "your-api-key"
      }
    }
  }
}
\`\`\`

## Available Tools

| Tool | Description |
|------|-------------|
| `notion_search` | Search pages and databases |
| `notion_get_page` | Get page content |
| `notion_create_page` | Create new page |
| `notion_update_page` | Update existing page |
| `notion_query_database` | Query database with filters |
```

---

### Prompt (Промпт)

**Файл:** `prompts/technical-writer.md`

```markdown
---
title: "Technical Documentation Writer"
description: "Системный промпт для написания технической документации"
tags:
  - documentation
  - technical-writing
  - api-docs
author: "VibeCoder"
---

You are a technical documentation specialist. Write clear, concise, and well-structured documentation.

## Style Guidelines

- Use active voice
- One idea per sentence
- Code examples for every concept
- Consistent terminology

## Documentation Structure

1. **Overview** — What and why
2. **Quick Start** — Get running in 5 minutes
3. **Concepts** — Core ideas explained
4. **API Reference** — Every endpoint/function
5. **Examples** — Real-world use cases
6. **Troubleshooting** — Common issues

## Code Examples Format

Always include:
- Language identifier
- Comments explaining non-obvious parts
- Expected output where relevant
```

---

### Bundle (Связка)

**Файл:** `bundles/fullstack-saas.md`

```markdown
---
title: "Fullstack SaaS Development Bundle"
description: "Полный набор для разработки SaaS-приложения: от бэкенда до деплоя"
tags:
  - fullstack
  - saas
  - startup
author: "VibeCoder"
category: "development"
mcps:
  - github
  - postgres
  - stripe
  - vercel
skills:
  - typescript-expert
  - react-developer
  - node-backend
agents:
  - code-reviewer
  - test-generator
prompts:
  - technical-writer
---

## What's Included

This bundle combines tools for building a complete SaaS application.

### Backend
- PostgreSQL for data storage
- Node.js/TypeScript expertise
- API design patterns

### Frontend
- React best practices
- TypeScript everywhere
- Modern CSS approaches

### DevOps
- GitHub integration
- Vercel deployment
- CI/CD setup

### Business
- Stripe for payments
- Analytics setup
```

---

## Изображения

**Не загружай изображения в репозиторий!** Используй только внешние URL.

### Где хостить

| Сервис | Бесплатно | Прямые ссылки |
|--------|-----------|---------------|
| [Imgur](https://imgur.com) | Да | Да |
| [Cloudinary](https://cloudinary.com) | 25GB | Да |
| [imgbb](https://imgbb.com) | Да | Да |
| GitHub Issues | Да | Да |

### Как вставить

```markdown
![Описание скриншота](https://i.imgur.com/abc123.png)
```

### Трюк с GitHub Issues

1. Открой любой Issue в любом репо
2. Перетащи картинку в поле комментария
3. Скопируй сгенерированный URL (не отправляй комментарий)
4. Используй URL в своём контенте

```markdown
![Demo](https://github.com/user-attachments/assets/abc123-def456.png)
```

### Рекомендации

- **Формат:** PNG для скриншотов, JPEG для фото
- **Размер:** до 1MB, ширина 800-1200px
- **Alt-текст:** всегда описывай что на картинке

---

## Формат Frontmatter

### Обязательные поля (все типы)

```yaml
---
title: "Название контента"
---
```

### Опциональные поля (все типы)

```yaml
description: "Описание до 200 символов"
tags:
  - tag1
  - tag2
author: "Имя автора"
featured: false  # true = показывать в featured секции
```

### Специфичные для Agents

```yaml
agent_name: "kebab-case-name"     # ID агента
agent_tools: "Read, Write, Bash"  # доступные инструменты
agent_model: "sonnet"             # sonnet | opus | haiku
```

### Специфичные для MCPs

```yaml
install_command: "npx -y @scope/package"
connection_type: "stdio"          # stdio | sse | websocket
paid_api: false                   # требуется ли платный API
```

### Специфичные для Bundles

```yaml
category: "marketing"             # категория бандла
mcps: [notion, github]            # slug'и MCP серверов
skills: [copywriting]             # slug'и навыков
agents: [content-writer]          # slug'и агентов
prompts: [blog-outline]           # slug'и промптов
```

---

## Валидация

GitHub Actions автоматически проверяет:

- Наличие обязательного поля `title`
- Корректность YAML синтаксиса
- Формат имени файла (kebab-case, латиница)

---

## Лицензия

**CC-BY-4.0** — можно использовать, изменять и распространять с указанием авторства.

---

## Связь

- **Сайт:** [vibebaza.com](https://vibebaza.com)
- **Telegram:** [@vibebaza](https://t.me/vibebaza)
- **Issues:** [GitHub Issues](https://github.com/aabulkhairov/vibebaza/issues)
