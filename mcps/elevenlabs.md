---
title: ElevenLabs MCP сервер
description: Model Context Protocol сервер, который интегрируется с ElevenLabs text-to-speech
  API для генерации аудио из текста, поддерживает множественные голоса, управление скриптами
  и постоянное хранение истории.
tags:
- AI
- Media
- API
- Storage
- Integration
author: Community
featured: false
install_command: npx -y @smithery/cli install elevenlabs-mcp-server --client claude
---

Model Context Protocol сервер, который интегрируется с ElevenLabs text-to-speech API для генерации аудио из текста, поддерживает множественные голоса, управление скриптами и постоянное хранение истории.

## Установка

### Smithery

```bash
npx -y @smithery/cli install elevenlabs-mcp-server --client claude
```

### uvx

```bash
uvx elevenlabs-mcp-server
```

### Из исходников

```bash
uv venv
```

## Конфигурация

### Конфигурация uvx

```json
{
  "mcpServers": {
    "elevenlabs": {
      "command": "uvx",
      "args": ["elevenlabs-mcp-server"],
      "env": {
        "ELEVENLABS_API_KEY": "your-api-key",
        "ELEVENLABS_VOICE_ID": "your-voice-id",
        "ELEVENLABS_MODEL_ID": "eleven_flash_v2",
        "ELEVENLABS_STABILITY": "0.5",
        "ELEVENLABS_SIMILARITY_BOOST": "0.75",
        "ELEVENLABS_STYLE": "0.1",
        "ELEVENLABS_OUTPUT_DIR": "output"
      }
    }
  }
}
```

### Конфигурация для разработки

```json
{
  "mcpServers": {
    "elevenlabs": {
      "command": "uv",
      "args": [
        "--directory",
        "path/to/elevenlabs-mcp-server",
        "run",
        "elevenlabs-mcp-server"
      ],
      "env": {
        "ELEVENLABS_API_KEY": "your-api-key",
        "ELEVENLABS_VOICE_ID": "your-voice-id",
        "ELEVENLABS_MODEL_ID": "eleven_flash_v2",
        "ELEVENLABS_STABILITY": "0.5",
        "ELEVENLABS_SIMILARITY_BOOST": "0.75",
        "ELEVENLABS_STYLE": "0.1",
        "ELEVENLABS_OUTPUT_DIR": "output"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate_audio_simple` | Генерация аудио из простого текста с использованием настроек голоса по умолчанию |
| `generate_audio_script` | Генерация аудио из структурированного скрипта с несколькими голосами и актерами |
| `delete_job` | Удаление задачи по её ID |
| `get_audio_file` | Получение аудиофайла по его ID |
| `list_voices` | Список всех доступных голосов |
| `get_voiceover_history` | Получение истории задач озвучивания. Опционально можно указать ID задачи для получения конкретной задачи |

## Возможности

- Генерация аудио из текста с использованием ElevenLabs API
- Поддержка множественных голосов и частей скрипта
- SQLite база данных для постоянного хранения истории
- Простое преобразование текста в речь
- Управление многочастными скриптами
- Отслеживание истории голосов и воспроизведение
- Загрузка аудиофайлов

## Переменные окружения

### Обязательные
- `ELEVENLABS_API_KEY` - ElevenLabs API ключ для аутентификации
- `ELEVENLABS_VOICE_ID` - ID голоса по умолчанию для использования

### Опциональные
- `ELEVENLABS_MODEL_ID` - ID модели ElevenLabs (по умолчанию: eleven_flash_v2)
- `ELEVENLABS_STABILITY` - Настройка стабильности голоса (по умолчанию: 0.5)
- `ELEVENLABS_SIMILARITY_BOOST` - Настройка усиления схожести (по умолчанию: 0.75)
- `ELEVENLABS_STYLE` - Настройка стиля (по умолчанию: 0.1)
- `ELEVENLABS_OUTPUT_DIR` - Директория вывода для сгенерированных аудиофайлов (по умолчанию: output)

## Ресурсы

- [GitHub Repository](https://github.com/mamertofabian/elevenlabs-mcp-server)

## Примечания

Включает в себя пример SvelteKit MCP Client веб-интерфейса для управления задачами генерации голоса. Сервер предоставляет ресурсы для истории озвучивания и голосов по адресам 'voiceover://history/{job_id}' и 'voiceover://voices' соответственно.