---
title: Office-Word-MCP-Server MCP сервер
description: MCP сервер для создания, чтения и обработки документов Microsoft Word, который позволяет AI-ассистентам работать с Word документами через стандартизированный интерфейс.
tags:
- Productivity
- Integration
- API
- Storage
- Code
author: GongRzhe
featured: true
---

MCP сервер для создания, чтения и обработки документов Microsoft Word, который позволяет AI-ассистентам работать с Word документами через стандартизированный интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @GongRzhe/Office-Word-MCP-Server --client claude
```

### Из исходников

```bash
git clone https://github.com/GongRzhe/Office-Word-MCP-Server.git
cd Office-Word-MCP-Server
pip install -r requirements.txt
```

### Скрипт установки

```bash
python setup_mcp.py
```

## Конфигурация

### Claude Desktop (локальная установка)

```json
{
  "mcpServers": {
    "word-document-server": {
      "command": "python",
      "args": ["/path/to/word_mcp_server.py"]
    }
  }
}
```

### Claude Desktop (используя uvx)

```json
{
  "mcpServers": {
    "word-document-server": {
      "command": "uvx",
      "args": ["--from", "office-word-mcp-server", "word_mcp_server"]
    }
  }
}
```

## Возможности

- Создание новых Word документов с метаданными
- Извлечение текста и анализ структуры документа
- Просмотр свойств документа и статистики
- Список доступных документов в директории
- Создание копий существующих документов
- Объединение нескольких документов в один
- Конвертация Word документов в PDF формат
- Добавление заголовков разных уровней с прямым форматированием
- Вставка параграфов с опциональным стилем и прямым форматированием
- Создание таблиц с пользовательскими данными

## Переменные окружения

### Опциональные
- `MCP_DEBUG` - Включает детальное логирование для отладки

## Примеры использования

```
Create a new document called 'report.docx' with a title page
```

```
Add a heading and three paragraphs to my document
```

```
Add my name in Helvetica 36pt bold at the top of the document
```

```
Add a section heading 'Summary' in Helvetica 14pt bold with a bottom border
```

```
Add a paragraph in Times New Roman 14pt with italic blue text
```

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/Office-Word-MCP-Server)

## Примечания

Требования: Python 3.8 или выше и менеджер пакетов pip. Расположение конфигурационного файла: macOS: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: %APPDATA%\Claude\claude_desktop_config.json. Перезапустите Claude for Desktop после изменения конфигурации. Сервер взаимодействует с файлами документов в вашей системе - всегда проверяйте запрашиваемые операции перед подтверждением.