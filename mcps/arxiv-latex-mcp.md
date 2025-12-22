---
title: arxiv-latex-mcp сервер
description: MCP сервер, который обеспечивает прямой доступ и обработку научных статей arXiv через получение исходного LaTeX кода, предоставляя точную интерпретацию математических выражений и уравнений, с которыми PDF часто справляются плохо.
tags:
- AI
- Search
- Analytics
- API
- Productivity
author: takashiishida
featured: false
---

MCP сервер, который обеспечивает прямой доступ и обработку научных статей arXiv через получение исходного LaTeX кода, предоставляя точную интерпретацию математических выражений и уравнений, с которыми PDF часто справляются плохо.

## Установка

### Расширения для десктопа (файл .dxt)

```bash
Download the .dxt file from releases and double-click to install (MacOS/Claude Desktop only)
```

### Ручная конфигурация

```bash
uv --directory /ABSOLUTE/PATH/TO/arxiv-latex-mcp run server/main.py
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "mcpServers": {
      "arxiv-latex-mcp": {
          "command": "uv",
          "args": [
              "--directory",
              "/ABSOLUTE/PATH/TO/arxiv-latex-mcp",
              "run",
              "server/main.py"
          ]
      }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_paper_prompt` | Получает и обрабатывает статьи arXiv из исходного LaTeX кода |

## Возможности

- Прямой доступ к исходному LaTeX коду arXiv
- Точная интерпретация математических выражений
- Лучшая обработка статей с большим количеством уравнений по сравнению с PDF
- Поддерживает Claude Desktop, Cursor и другие MCP клиенты
- Использует arxiv-to-prompt для обработки LaTeX

## Примеры использования

```
Explain the first theorem in 2202.00395
```

## Ресурсы

- [GitHub Repository](https://github.com/takashiishida/arxiv-latex-mcp)

## Примечания

Особенно полезен для статей по информатике, математике и инженерным наукам. Возможно, потребуется заменить поле 'command' на полный путь к 'uv' (проверьте с помощью 'which uv' на MacOS/Linux или 'where uv' на Windows). Перезапустите приложение после конфигурации.