---
title: Fish Audio MCP сервер
description: MCP сервер, который обеспечивает бесшовную интеграцию между Text-to-Speech API от Fish Audio и LLM вроде Claude, предоставляя возможности синтеза речи на естественном языке с клонированием голоса, мультиязычной поддержкой и потоковыми возможностями.
tags:
- AI
- Media
- API
- Integration
author: da-okazaki
featured: false
---

MCP сервер, который обеспечивает бесшовную интеграцию между Text-to-Speech API от Fish Audio и LLM вроде Claude, предоставляя возможности синтеза речи на естественном языке с клонированием голоса, мультиязычной поддержкой и потоковыми возможностями.

## Установка

### NPX (Прямой запуск)

```bash
npx @alanse/fish-audio-mcp-server
```

### Глобальная установка через NPM

```bash
npm install -g @alanse/fish-audio-mcp-server
```

### Из исходников

```bash
git clone https://github.com/da-okazaki/mcp-fish-audio-server.git
cd mcp-fish-audio-server
npm install
npm run build
npm run dev
```

## Конфигурация

### Режим одного голоса

```json
{
  "mcpServers": {
    "fish-audio": {
      "command": "npx",
      "args": ["-y", "@alanse/fish-audio-mcp-server"],
      "env": {
        "FISH_API_KEY": "your_fish_audio_api_key_here",
        "FISH_MODEL_ID": "speech-1.6",
        "FISH_REFERENCE_ID": "your_voice_reference_id_here",
        "FISH_OUTPUT_FORMAT": "mp3",
        "FISH_STREAMING": "false",
        "FISH_LATENCY": "balanced",
        "FISH_MP3_BITRATE": "128",
        "FISH_AUTO_PLAY": "false",
        "AUDIO_OUTPUT_DIR": "~/.fish-audio-mcp/audio_output"
      }
    }
  }
}
```

### Режим нескольких голосов

```json
{
  "mcpServers": {
    "fish-audio": {
      "command": "npx",
      "args": ["-y", "@alanse/fish-audio-mcp-server"],
      "env": {
        "FISH_API_KEY": "your_fish_audio_api_key_here",
        "FISH_MODEL_ID": "speech-1.6",
        "FISH_REFERENCES": "[{'reference_id':'id1','name':'Alice','tags':['female','english']},{'reference_id':'id2','name':'Bob','tags':['male','japanese']},{'reference_id':'id3','name':'Carol','tags':['female','japanese','anime']}]",
        "FISH_DEFAULT_REFERENCE": "id1",
        "FISH_OUTPUT_FORMAT": "mp3",
        "FISH_STREAMING": "false",
        "FISH_LATENCY": "balanced",
        "FISH_MP3_BITRATE": "128",
        "FISH_AUTO_PLAY": "false",
        "AUDIO_OUTPUT_DIR": "~/.fish-audio-mcp/audio_output"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `fish_audio_tts` | Генерирует речь из текста с использованием TTS API от Fish Audio с поддержкой кастомных голосов, потокового вещания... |
| `fish_audio_list_references` | Показывает все настроенные голосовые референсы с их ID, именами и тегами |

## Возможности

- Высококачественный TTS с современным синтезом речи
- Потоковая поддержка для стрима аудио в реальном времени и приложений с низкой задержкой
- Поддержка нескольких голосов с кастомными голосовыми моделями через референс ID
- Умный выбор голоса по ID, имени или тегам
- Управление голосовой библиотекой для настройки и управления несколькими голосовыми референсами
- Поддержка множества аудиоформатов (MP3, WAV, PCM, Opus)
- Возможности клонирования голоса для создания кастомных голосовых моделей
- Мультиязычная поддержка включая английский, японский, китайский и другие
- WebSocket стрим в реальном времени с живым воспроизведением
- Гибкая конфигурация через переменные окружения

## Переменные окружения

### Обязательные
- `FISH_API_KEY` - Ваш API ключ Fish Audio

### Опциональные
- `FISH_MODEL_ID` - TTS модель для использования (s1, speech-1.5, speech-1.6)
- `FISH_REFERENCE_ID` - ID голосового референса по умолчанию (режим одного референса)
- `FISH_REFERENCES` - Множественные голосовые референсы в формате JSON
- `FISH_DEFAULT_REFERENCE` - ID референса по умолчанию при использовании нескольких референсов
- `FISH_OUTPUT_FORMAT` - Формат аудио по умолчанию (mp3, wav, pcm, opus)
- `FISH_STREAMING` - Включить потоковый режим (HTTP/WebSocket)
- `FISH_LATENCY` - Режим задержки (normal, balanced)
- `FISH_MP3_BITRATE` - Битрейт MP3 (64, 128, 192)

## Примеры использования

```
Сгенерируй речь с текстом 'Привет, мир! Добро пожаловать в Fish Audio TTS.'
```

```
Сгенерируй речь с голосовой моделью xyz123 с текстом 'Это тест кастомного голоса'
```

```
Используй голос Alice чтобы сказать 'Привет от Alice'
```

```
Сгенерируй японскую речь с текстом 'こんにちは' аниме голосом
```

```
Какие голоса доступны?
```

## Ресурсы

- [GitHub Repository](https://github.com/da-okazaki/mcp-fish-audio-server)

## Примечания

Требуется API ключ Fish Audio. Поддерживает до 10,000 символов на TTS запрос. Приоритет выбора голоса: reference_id > reference_name > reference_tag > по умолчанию. Включает обработку ошибок для лимитов API, проблем с сетью и некорректных параметров.