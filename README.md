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

## Формат контента

Каждый файл — это Markdown с YAML frontmatter:

```markdown
---
title: "Название"
description: "Краткое описание (до 200 символов)"
tags:
  - тег1
  - тег2
author: "Автор"
featured: false
---

Содержимое в формате Markdown...
```

### Дополнительные поля по типам

**Agents:**
```yaml
agent_name: "my-agent"
agent_tools: "Read, Write, Glob, Grep, Bash"
agent_model: "sonnet"  # sonnet | opus | haiku
```

**MCPs:**
```yaml
install_command: "npx -y @scope/package"
connection_type: "stdio"
paid_api: false
```

**Bundles:**
```yaml
category: "marketing"
mcps: [notion, firecrawl]
skills: [content-marketing]
agents: [seo-agent]
prompts: [blog-outline]
```

## Как добавить свой контент

См. [CONTRIBUTING.md](CONTRIBUTING.md)

## Лицензия

CC-BY-4.0 — можно использовать, изменять и распространять с указанием авторства.
