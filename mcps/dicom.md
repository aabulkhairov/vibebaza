---
title: Dicom MCP сервер
description: MCP сервер, который позволяет AI-ассистентам запрашивать, читать и перемещать данные на DICOM серверах (PACS, VNA и т.д.) для систем медицинской визуализации, включая извлечение текста из DICOM-инкапсулированных PDF отчетов.
tags:
- Database
- AI
- Analytics
- Integration
- API
author: ChristianHinge
featured: false
---

MCP сервер, который позволяет AI-ассистентам запрашивать, читать и перемещать данные на DICOM серверах (PACS, VNA и т.д.) для систем медицинской визуализации, включая извлечение текста из DICOM-инкапсулированных PDF отчетов.

## Установка

### Установка через UV Tool

```bash
uv tool install dicom-mcp
```

### Из исходного кода

```bash
git clone https://github.com/ChristianHinge/dicom-mcp
cd dicom mcp
uv venv
source .venv/bin/activate
uv pip install -e ".[dev]"
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "dicom": {
      "command": "uv",
      "args": ["tool","dicom-mcp", "/path/to/your_config.yaml"]
    }
  }
}
```

### Разработка

```json
{
    "mcpServers": {
        "arxiv-mcp-server": {
            "command": "uv",
            "args": [
                "--directory",
                "path/to/cloned/dicom-mcp",
                "run",
                "dicom-mcp",
                "/path/to/your_config.yaml"
            ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `query_patients` | Поиск пациентов по критериям вроде имени, ID или даты рождения |
| `query_studies` | Поиск исследований по ID пациента, дате, модальности, описанию, номеру доступа или Study UID |
| `query_series` | Поиск серий в конкретном исследовании по модальности, номеру/описанию серии или Series UID |
| `query_instances` | Поиск отдельных экземпляров (изображений/объектов) в серии по номеру экземпляра или SOP Instance UID |
| `extract_pdf_text_from_dicom` | Получение конкретного DICOM экземпляра с инкапсулированным PDF и извлечение его текстового содержимого |
| `move_series` | Отправка конкретной DICOM серии на другой настроенный DICOM узел через C-MOVE |
| `move_study` | Отправка целого DICOM исследования на другой настроенный DICOM узел через C-MOVE |
| `list_dicom_nodes` | Показ текущего активного DICOM узла и список всех настроенных узлов |
| `switch_dicom_node` | Переключение активного DICOM узла для последующих операций |
| `verify_connection` | Тестирование DICOM сетевого соединения с текущим активным узлом через C-ECHO |
| `get_attribute_presets` | Список доступных уровней детализации (минимальный, стандартный, расширенный) для результатов запросов метаданных |

## Возможности

- Запрос метаданных: Поиск пациентов, исследований, серий и экземпляров по различным критериям
- Чтение DICOM отчетов (PDF): Получение DICOM экземпляров с инкапсулированными PDF и извлечение текстового содержимого
- Отправка DICOM изображений: Отправка серий или исследований в другие DICOM места назначения для AI обработки
- Управление соединениями и понимание опций запросов с помощью утилит

## Примеры использования

```
Any significant findings in John Doe's previous CT report?
```

```
What's the volume of his spleen at the last scan and the scan today?
```

## Ресурсы

- [GitHub Repository](https://github.com/ChristianHinge/dicom-mcp)

## Примечания

Требует YAML файл конфигурации, определяющий DICOM узлы и вызывающие AE titles. ВНИМАНИЕ: Не предназначен для клинического использования и не должен подключаться к активным больничным базам данных или базам данных с конфиденциальными данными пациентов.