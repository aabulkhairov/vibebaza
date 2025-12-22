---
title: Masquerade MCP сервер
description: MCP сервер приватности, который автоматически обнаруживает и скрывает
  конфиденциальные данные (имена, email, даты, сущности) из PDF документов перед отправкой
  их в LLM модели вроде Claude.
tags:
- Security
- AI
- Productivity
- Analytics
author: Community
featured: false
---

MCP сервер приватности, который автоматически обнаруживает и скрывает конфиденциальные данные (имена, email, даты, сущности) из PDF документов перед отправкой их в LLM модели вроде Claude.

## Установка

### Автоматическая установка

```bash
curl -O https://raw.githubusercontent.com/postralai/masquerade/main/setup.sh && bash setup.sh
```

### Ручная установка

```bash
python3.12 -m venv pdfmcp
source pdfmcp/bin/activate
pip install git+https://github.com/postralai/masquerade@main
python -m masquerade.configure_claude
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "pdf-redaction": {
      "command": "/path/to/python",
      "args": ["/path/to/mcp_pdf_redaction.py"],
      "env": {
        "TINFOIL_API_KEY": "your_api_key"
      }
    }
  }
}
```

## Возможности

- Автоматическое обнаружение конфиденциальных данных (имена, email, даты, сущности)
- Сокрытие конфиденциальных данных из PDF документов
- Предварительный просмотр скрытых данных перед отправкой в LLM
- Создание отредактированных PDF файлов с выделенными конфиденциальными областями
- Предоставление сводки с замаскированными конфиденциальными данными и количеством скрытий на странице
- Использует изолированную AI платформу (Tinfoil с Llama 3.3 70B) для обнаружения конфиденциальных данных

## Переменные окружения

### Обязательные
- `TINFOIL_API_KEY` - API ключ для платформы Tinfoil, используемой для обнаружения конфиденциальных данных

## Примеры использования

```
Redact sensitive information from this PDF: /path/to/filename.pdf
```

## Ресурсы

- [GitHub Repository](https://github.com/postralai/masquerade)

## Примечания

Требует Python >=3.10, <=3.12. Пользователям необходимо создать аккаунт Tinfoil и API ключ. Не загружайте оригинальный PDF в Claude, предоставляйте только путь к файлу для редактирования.