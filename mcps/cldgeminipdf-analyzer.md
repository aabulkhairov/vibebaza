---
title: CLDGeminiPDF Analyzer MCP сервер
description: MCP сервер, который позволяет Claude Desktop анализировать PDF документы с помощью AI моделей Google Gemini, поддерживающий как прямую загрузку PDF, так и методы извлечения текста.
tags:
- AI
- API
- Productivity
- Integration
- Analytics
author: Community
featured: false
---

MCP сервер, который позволяет Claude Desktop анализировать PDF документы с помощью AI моделей Google Gemini, поддерживающий как прямую загрузку PDF, так и методы извлечения текста.

## Установка

### Скачать готовый JAR файл

```bash
Download the latest CLDGeminiPDF.v1.0.0.jar from the Releases page
```

### Сборка из исходников

```bash
git clone <your-repository-url>
cd CLDGeminiPDF
mvn clean compile assembly:single
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/path/to/your/documents"
      ]
    },
    "CLDGeminiPDF": {
      "command": "java",
      "args": [
        "-jar",
        "/path/to/CLDGeminiPDF.v1.0.0.jar"
      ],
      "env": {
        "GEMINI_API_KEY": "your_api_key_here",
        "GEMINI_MODEL": "gemini-2.0-flash"
      }
    }
  }
}
```

## Возможности

- Анализ PDF: Извлечение и анализ содержимого PDF с использованием AI моделей Gemini
- Поддержка множества моделей: Выбор из различных моделей Gemini (серии 2.5, 2.0, 1.5 и модели Gemma)
- Два метода обработки: Прямая загрузка PDF в Gemini или резервное извлечение текста
- Интеграция MCP: Бесшовная интеграция с Claude Desktop через Model Context Protocol
- Гибкая конфигурация: Конфигурация через переменные окружения для удобного деплоя

## Переменные окружения

### Обязательные
- `GEMINI_API_KEY` - API ключ Google AI Studio для доступа к моделям Gemini

### Опциональные
- `GEMINI_MODEL` - Конкретная модель Gemini для использования (например, gemini-2.0-flash)

## Примеры использования

```
Please analyze this research paper: file:///Users/username/Documents/research_paper.pdf Focus on the methodology and conclusions.
```

```
Find the "research_paper.pdf" file in the Documents directory and analyze it using Gemini.
```

```
What Gemini models are available for PDF analysis?
```

```
Analyze this contract using the gemini-2.5-pro model: file:///path/to/contract.pdf Look for key terms and potential risks.
```

```
List the available Gemini models
```

## Ресурсы

- [GitHub Repository](https://github.com/tfll37/CLDGeminiPDF-Analyzer)

## Примечания

Требует Java 11 или выше и Filesystem MCP сервер как зависимость. Версия 1.0.0 НЕ поддерживает drag-and-drop файлы - файлы должны быть доступны через filesystem сервер. Пользователи бесплатного тарифа имеют различные лимиты для разных моделей Gemini.