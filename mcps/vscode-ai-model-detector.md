---
title: vscode-ai-model-detector MCP сервер
description: Расширение для Visual Studio Code, которое обеспечивает обнаружение и классификацию AI моделей в режиме реального времени, используемых в GitHub Copilot и других расширениях с поддержкой ИИ. Поддерживает точную идентификацию моделей через встроенное хранилище и настройки VS Code.
tags:
- AI
- Code
- Productivity
- Monitoring
- API
author: Community
featured: false
---

Расширение для Visual Studio Code, которое обеспечивает обнаружение и классификацию AI моделей в режиме реального времени, используемых в GitHub Copilot и других расширениях с поддержкой ИИ. Поддерживает точную идентификацию моделей через встроенное хранилище и настройки VS Code.

## Установка

### VS Code Marketplace

```bash
1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Search for "AI Model Detector"
4. Click Install
```

## Возможности

- Обнаружение моделей в реальном времени: Точно определяет текущую AI модель из хранилища приложения VS Code
- Динамический реестр моделей: Поддерживает более 41 ID моделей от основных провайдеров ИИ
- Высокая производительность: Прямая интеграция с SQLite хранилищем VS Code
- Комплексная классификация: Определяет семейство моделей, вендора и возможности
- Обновления в реальном времени: Отслеживает изменения моделей в режиме live
- Высокоточное обнаружение: Использует реальные настройки VS Code и Chat Participant API
- Поддержка множественных установок: Работает с VS Code Stable, Insiders и VSCodium

## Примеры использования

```
Detect current AI model being used in VS Code
```

```
Monitor AI model changes in real-time with custom intervals
```

```
Get model capabilities and metadata for specific AI models
```

```
Identify model family, vendor, token limits, and context windows
```

## Ресурсы

- [GitHub Repository](https://github.com/thisis-romar/vscode-ai-model-detector)

## Примечания

Требует Visual Studio Code >= 1.85.0, расширение GitHub Copilot для обнаружения моделей Copilot, и активное AI расширение, использующее Chat Participant API VS Code. Поддерживает серии OpenAI GPT, Anthropic Claude, Google Gemini и другие модели. Следует стандарту GIT-ATT-001 v1.1.0 для атрибуции ИИ в коммитах.