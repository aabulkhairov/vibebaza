---
title: TuriX Computer Automation MCP сервер
description: MCP сервер, который позволяет AI агентам выполнять задачи автоматизации рабочего стола, совершая прямые действия на вашем компьютере, включая клики, набор текста и управление приложениями в macOS и Windows.
tags:
- AI
- Productivity
- Integration
- Browser
- API
author: TurixAI
featured: false
---

MCP сервер, который позволяет AI агентам выполнять задачи автоматизации рабочего стола, совершая прямые действия на вашем компьютере, включая клики, набор текста и управление приложениями в macOS и Windows.

## Установка

### Из исходного кода

```bash
git clone https://github.com/TurixAI/TuriX-CUA
conda create -n turix_env python=3.12
conda activate turix_env
pip install -r requirements.txt
```

### Настройка для Windows

```bash
git checkout windows
```

## Конфигурация

### Конфигурация задач

```json
{
    "agent": {
         "task": "open system settings, switch to Dark Mode"
    }
}
```

### Конфигурация API

```json
{
   "llm": {
      "provider": "turix",
      "api_key": "YOUR_API_KEY",
      "base_url": "https://llm.turixapi.io/v1"
   }
}
```

## Возможности

- Современный агент для работы с компьютером с >68% успешности в OSWorld-подобных тестах
- Кроссплатформенная поддержка macOS и Windows
- Горячая замена AI моделей через config.json
- MCP интеграция с Claude Desktop и другими агентами
- Не требует специфичных для приложений API - работает с любым кликабельным интерфейсом
- Поддержка модели Qwen3-VL vision-language
- С открытым исходным кодом и бесплатный для личного использования и исследований

## Примеры использования

```
Book a flight, hotel and uber
```

```
Search iPhone price, create Pages document, and send to contact
```

```
Generate a bar-chart in Numbers file and insert it to PowerPoint
```

```
Search video content in YouTube and like it
```

```
Open system settings, switch to Dark Mode
```

## Ресурсы

- [GitHub Repository](https://github.com/TurixAI/TuriX-CUA)

## Примечания

Требует специальных разрешений macOS (Accessibility и Safari Automation). Пользователи Windows должны использовать ветку 'windows'. Агентом можно управлять через протокол MCP, он интегрируется с Claude Desktop. Бенчмарки производительности показывают превосходные результаты по сравнению с предыдущими агентами с открытым исходным кодом, такими как UI-TARS.