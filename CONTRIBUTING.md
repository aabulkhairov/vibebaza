# Как внести вклад

Спасибо за желание улучшить VibeBaza Library!

## Быстрый старт

1. **Fork** этого репозитория
2. **Clone** свой форк: `git clone https://github.com/YOUR_USERNAME/vibebaza.git`
3. Создай файл в нужной папке
4. **Commit & Push** в свой форк
5. Открой **Pull Request**

## Структура файлов

```
{тип}/{slug}.md
```

- `slug` — имя файла без расширения, используется в URL
- Используй kebab-case: `my-awesome-prompt.md`
- Только латиница в имени файла

## Обязательные поля

Каждый файл должен содержать YAML frontmatter:

```yaml
---
title: "Название на русском или английском"
---
```

## Опциональные поля (все типы)

```yaml
description: "Краткое описание до 200 символов"
tags:
  - тег1
  - тег2
author: "Твоё имя или ник"
featured: false
```

## Поля для агентов

```yaml
agent_name: "kebab-case-name"
agent_tools: "Read, Write, Glob, Grep, Bash, WebSearch"
agent_model: "sonnet"  # sonnet | opus | haiku
```

## Поля для MCP

```yaml
install_command: "npx -y @scope/package --client claude"
connection_type: "stdio"
paid_api: false  # true если нужен платный API
```

## Изображения

Используй только внешние URL:

```markdown
![Описание](https://cdn.example.com/image.png)
```

Не добавляй изображения в репозиторий — загружай на:
- [Imgur](https://imgur.com)
- [Cloudinary](https://cloudinary.com)
- Или свой хостинг

## Процесс проверки

1. GitHub Actions автоматически проверит формат
2. Мейнтейнер просмотрит содержимое
3. После одобрения — merge в main
4. Контент появится на vibebaza.com

## Что принимаем

- Полезные промпты и навыки
- Рабочие конфигурации агентов
- Документация MCP-серверов
- Исправления ошибок и опечаток
- Улучшения описаний

## Что НЕ принимаем

- Спам и реклама
- Вредоносный контент
- Плагиат без указания источника
- Контент нарушающий ToS Anthropic

## Вопросы?

Открой Issue или напиши в [Telegram](https://t.me/vibebaza).
