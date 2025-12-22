---
title: VoiceMode MCP сервер
description: Естественные голосовые разговоры для AI-помощников. VoiceMode добавляет человекоподобные голосовые взаимодействия в Claude Code и AI редакторы кода через Model Context Protocol (MCP).
tags:
- AI
- Media
- Integration
- Productivity
author: Community
featured: false
install_command: claude mcp add --scope user voicemode -- uvx --refresh voice-mode
---

Естественные голосовые разговоры для AI-помощников. VoiceMode добавляет человекоподобные голосовые взаимодействия в Claude Code и AI редакторы кода через Model Context Protocol (MCP).

## Установка

### UV Tool Install

```bash
uv tool install voice-mode
```

### Быстрая установка с зависимостями

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uvx voice-mode-install
export OPENAI_API_KEY=your-openai-key
claude mcp add --scope user voicemode -- uvx --refresh voice-mode
claude converse
```

### Claude Code (CLI)

```bash
claude mcp add --scope user voicemode uvx --refresh voice-mode
```

### Из исходного кода

```bash
git clone https://github.com/mbailey/voicemode.git
cd voicemode
uv tool install -e .
```

### NixOS Profile Install

```bash
nix profile install github:mbailey/voicemode
```

## Конфигурация

### Claude Code с переменными окружения

```json
claude mcp add --scope user --env OPENAI_API_KEY=your-openai-key voicemode -- uvx --refresh voice-mode
```

## Возможности

- Естественные голосовые разговоры с Claude Code - задавайте вопросы и слушайте ответы
- Поддерживает локальные голосовые модели - работает с любыми STT/TTS сервисами, совместимыми с OpenAI API
- Режим реального времени - низкая задержка голосовых взаимодействий с автоматическим выбором транспорта
- MCP интеграция - бесшовная работа с Claude Code (и другими MCP клиентами)
- Обнаружение тишины - автоматически останавливает запись, когда вы прекращаете говорить
- Множественные транспорты - локальный микрофон или коммуникация через LiveKit комнату (опционально)

## Переменные окружения

### Опциональные
- `OPENAI_API_KEY` - OpenAI API ключ для сервисов преобразования речи в текст и текста в речь
- `VOICEMODE_SAVE_AUDIO` - Сохранять все аудиофайлы (как TTS вывод, так и STT ввод)

## Примеры использования

```
Start a voice conversation with Claude using 'claude converse'
```

```
Ask questions verbally and hear responses through voice interactions
```

```
Use natural speech for coding assistance and AI conversations
```

## Ресурсы

- [GitHub Repository](https://github.com/mbailey/voicemode)

## Примечания

Поддерживает Python 3.10-3.14. Работает на Linux, macOS, Windows (WSL) и NixOS. Требует системные аудио-зависимости (ffmpeg, portaudio и т.д.) и микрофон/динамики. LiveKit интеграция опциональна и требует Python 3.10-3.13. Локальные STT/TTS сервисы (Whisper.cpp, Kokoro) доступны для использования с акцентом на приватность.