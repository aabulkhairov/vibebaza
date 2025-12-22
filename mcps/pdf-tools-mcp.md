---
title: PDF Tools MCP сервер
description: Комплексный инструментарий для работы с PDF, который интегрируется с Claude AI через MCP, позволяя выполнять операции с PDF файлами такие как объединение, разделение, шифрование, оптимизация и анализ через команды на естественном языке.
tags:
- Productivity
- Security
- Media
- AI
author: Community
featured: false
---

Комплексный инструментарий для работы с PDF, который интегрируется с Claude AI через MCP, позволяя выполнять операции с PDF файлами такие как объединение, разделение, шифрование, оптимизация и анализ через команды на естественном языке.

## Установка

### С виртуальным окружением (рекомендуется)

```bash
git clone https://github.com/Sohaib-2/pdf-mcp-server.git
cd pdf-mcp-server
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
pip install -r requirements.txt
```

### Без виртуального окружения

```bash
git clone https://github.com/Sohaib-2/pdf-mcp-server.git
cd pdf-mcp-server
pip install fastmcp requests pathlib
```

### Установка PDF инструментов - PDFtk

```bash
# Ubuntu/Debian
sudo apt-get install pdftk
# macOS
brew install pdftk-java
# Windows: Download from https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/
```

### Установка PDF инструментов - QPDF

```bash
# Ubuntu/Debian
sudo apt-get install qpdf
# macOS
brew install qpdf
# Windows: Download from https://qpdf.sourceforge.io/
```

## Конфигурация

### Claude Desktop (Windows с виртуальным окружением)

```json
{
  "mcpServers": {
    "pdf-tools": {
      "command": "C:\\path\\to\\pdf-mcp-server\\.venv\\Scripts\\python.exe",
      "args": ["C:\\path\\to\\pdf-mcp-server\\server.py"]
    }
  }
}
```

### Claude Desktop (без виртуального окружения)

```json
{
  "mcpServers": {
    "pdf-tools": {
      "command": "python",
      "args": ["C:\\path\\to\\pdf-mcp-server\\server.py"]
    }
  }
}
```

### Claude Desktop (macOS/Linux с venv)

```json
{
  "mcpServers": {
    "pdf-tools": {
      "command": "/path/to/pdf-mcp-server/.venv/bin/python",
      "args": ["/path/to/pdf-mcp-server/server.py"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `merge_pdfs` | Объединение нескольких PDF в один документ |
| `split_pdf` | Разделение PDF на отдельные страницы |
| `extract_pages` | Извлечение определенных диапазонов страниц из PDF |
| `rotate_pages` | Поворот страниц на указанное количество градусов |
| `encrypt_pdf` | Применение AES-256 шифрования к PDF |
| `encrypt_pdf_basic` | Добавление базовой парольной защиты к PDF |
| `decrypt_pdf` | Снятие парольной защиты с PDF |
| `optimize_pdf` | Сжатие PDF для веб/email доставки |
| `repair_pdf` | Исправление поврежденных PDF файлов |
| `check_pdf_integrity` | Проверка структуры и целостности PDF |
| `get_pdf_info` | Получение детальных метаданных PDF в JSON формате |
| `update_pdf_metadata` | Изменение заголовка PDF, автора и других метаданных |
| `inspect_pdf_structure` | Анализ внутренней структуры PDF |
| `extract_pdf_attachments` | Извлечение встроенных файлов из PDF |
| `download_pdf` | Скачивание PDF по URL |

## Возможности

- AI-управляемые команды для работы с PDF на естественном языке через интеграцию с Claude
- Объединение, разделение и извлечение страниц из PDF
- AES-256 шифрование и парольная защита
- Оптимизация и сжатие PDF
- Восстановление поврежденных PDF файлов
- Извлечение и анализ метаданных PDF
- Скачивание PDF по URLs
- Гибкое разрешение путей к файлам с несколькими директориями поиска
- Поддержка как PDFtk, так и QPDF бэкендов
- Полный анализ структуры PDF и проверка целостности

## Переменные окружения

### Опциональные
- `PDF_WORKSPACE` - Пользовательская рабочая директория для операций с PDF (первая в порядке поиска)

## Примеры использования

```
Объедини эти 3 PDF в один документ
```

```
Зашифруй мой отчет с парольной защитой
```

```
Извлеки страницы 1-10 из этого руководства
```

```
Объедини все мои научные работы в одну библиографию
```

```
Раздели это 100-страничное руководство на главы
```

## Ресурсы

- [GitHub Repository](https://github.com/Sohaib-2/pdf-mcp-server)

## Примечания

Требует отдельной установки PDFtk и QPDF. Поддерживает гибкое разрешение путей к файлам с директориями поиска по умолчанию включая ~/Documents/PDFs, ~/Downloads, ~/Desktop и текущую рабочую директорию. Построен на фреймворке FastMCP и предоставляет 16 всеобъемлющих инструментов для работы с PDF.