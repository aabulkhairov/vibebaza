---
title: joinly MCP сервер
description: MCP сервер, который позволяет AI агентам присоединяться и активно участвовать в видеозвонках в Google Meet, Zoom и Microsoft Teams через автоматизацию браузера, предоставляя живые транскрипты, голосовое взаимодействие и возможности чата.
tags:
- Browser
- AI
- Productivity
- Integration
- Media
author: joinly-ai
featured: true
---

MCP сервер, который позволяет AI агентам присоединяться и активно участвовать в видеозвонках в Google Meet, Zoom и Microsoft Teams через автоматизацию браузера, предоставляя живые транскрипты, голосовое взаимодействие и возможности чата.

## Установка

### Docker

```bash
docker pull ghcr.io/joinly-ai/joinly:latest
docker run --env-file .env ghcr.io/joinly-ai/joinly:latest --client <MeetingURL>
```

### Внешний клиент

```bash
docker run -p 8000:8000 ghcr.io/joinly-ai/joinly:latest
uvx joinly-client --env-file .env <MeetingUrl>
```

### Поддержка GPU

```bash
docker pull ghcr.io/joinly-ai/joinly:latest-cuda
docker run --gpus all --env-file .env -p 8000:8000 ghcr.io/joinly-ai/joinly:latest-cuda
```

## Конфигурация

### Переменные окружения

```json
# .env
# для OpenAI LLM
JOINLY_LLM_MODEL=gpt-4o
JOINLY_LLM_PROVIDER=openai
OPENAI_API_KEY=your-openai-api-key
```

### Конфигурация MCP серверов

```json
{
    "mcpServers": {
        "localServer": {
            "command": "npx",
            "args": ["-y", "package@0.1.0"]
        },
        "remoteServer": {
            "url": "http://mcp.example.com",
            "auth": "oauth"
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `join_meeting` | Присоединиться к встрече с URL, именем участника и опциональным паролем |
| `leave_meeting` | Покинуть текущую встречу |
| `speak_text` | Произнести текст используя TTS (требует параметр text) |
| `send_chat_message` | Отправить сообщение в чат (требует параметр message) |
| `mute_yourself` | Отключить микрофон |
| `unmute_yourself` | Включить микрофон |
| `get_chat_history` | Получить историю чата текущей встречи в формате JSON |
| `get_participants` | Получить участников текущей встречи в формате JSON |
| `get_transcript` | Получить транскрипт текущей встречи в формате JSON, опционально отфильтрованный по минутам |
| `get_video_snapshot` | Получить изображение с текущей встречи, например, посмотреть текущий показ экрана |

## Возможности

- Живое взаимодействие: Позволяет агентам выполнять задачи и отвечать в реальном времени голосом или через чат во время встреч
- Разговорный поток: Встроенная логика, которая обеспечивает естественные разговоры, обрабатывая прерывания и взаимодействие нескольких говорящих
- Кроссплатформенность: Присоединение к Google Meet, Zoom и Microsoft Teams (или любой платформе, доступной через браузер)
- Принеси-свой-LLM: Работает со всеми провайдерами LLM (также локально с Ollama)
- Выбери-предпочитаемый-TTS/STT: Модульный дизайн поддерживает множество сервисов - Whisper/Deepgram для STT и Kokoro/ElevenLabs/Deepgram для TTS
- 100% open-source, самохостинг и privacy-first

## Переменные окружения

### Обязательные
- `JOINLY_LLM_MODEL` - Модель LLM для использования (например, gpt-4o)
- `JOINLY_LLM_PROVIDER` - Провайдер LLM (openai, anthropic, ollama)

### Опциональные
- `OPENAI_API_KEY` - API ключ OpenAI для GPT моделей
- `ELEVENLABS_API_KEY` - API ключ ElevenLabs для TTS
- `DEEPGRAM_API_KEY` - API ключ Deepgram для STT/TTS

## Примеры использования

```
Присоединиться к встрече и отвечать на вопросы, получая доступ к последним новостям из интернета
```

```
Создавать задачи GitHub во время встреч на основе обсуждений
```

```
Редактировать содержимое страниц Notion в реальном времени во время встреч
```

```
Получать транскрипты встреч и информацию об участниках
```

```
Отправлять сообщения в чат и озвучивать ответы во время видеозвонков
```

## Ресурсы

- [GitHub Repository](https://github.com/joinly-ai/joinly)

## Примечания

Предоставляет ресурс живого транскрипта (transcript://live), на который можно подписаться для получения обновлений в реальном времени. Поддерживает ускорение GPU с CUDA для лучшего качества транскрипции. Может работать как автономный клиент или как MCP сервер с подключающимися к нему внешними клиентами.