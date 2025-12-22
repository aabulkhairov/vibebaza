---
title: OneNote MCP сервер
description: MCP сервер, который предоставляет AI-ассистентам доступ к Microsoft OneNote,
  позволяя читать и записывать данные в блокноты, разделы и страницы OneNote с помощью
  Microsoft Graph API.
tags:
- Productivity
- API
- Integration
- Storage
- Cloud
author: rajvirtual
featured: false
---

MCP сервер, который предоставляет AI-ассистентам доступ к Microsoft OneNote, позволяя читать и записывать данные в блокноты, разделы и страницы OneNote с помощью Microsoft Graph API.

## Установка

### Из исходного кода

```bash
git clone [repository]
npm install
npm run build
npm start
```

### Docker

```bash
mkdir -p data
docker build -t onenote-mcp-server .
docker run -d --name onenote-mcp-server -e CLIENT_ID=your-client-id -v $(pwd)/data:/app/dist onenote-mcp-server
```

## Конфигурация

### Claude Desktop

```json
Set the server directory to your cloned repository
Set the command to: npm run build && npm start
Add environment variable:
- Name: CLIENT_ID
- Value: [Your Microsoft Azure Application Client ID]
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `onenote-read` | Чтение контента из блокнотов, разделов или страниц Microsoft OneNote с опциональными метаданными и содержимым... |
| `onenote-create` | Создание нового контента в Microsoft OneNote, включая страницы, разделы или блокноты с HTML-содержимым... |

## Возможности

- Чтение блокнотов, разделов и страниц из OneNote
- Создание новых блокнотов, разделов и страниц в OneNote
- Конвертация HTML-контента в текст для улучшенной обработки RAG
- Аутентификация через device code flow с Microsoft Graph API
- Кэширование токенов для постоянной аутентификации
- Поддержка Docker для контейнерного деплоя

## Переменные окружения

### Обязательные
- `CLIENT_ID` - Ваш Client ID приложения Microsoft Azure для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/rajvirtual/MCP-Servers)

## Примечания

Требует аккаунт Microsoft Azure с зарегистрированным приложением и разрешениями API (Notes.Read, Notes.ReadWrite). Использует аутентификацию через device code flow - при первом запуске генерируется код, сохраняемый в device-code.txt, который необходимо ввести по предоставленному URL. Токены кэшируются в token-cache.json для дальнейшего использования.