---
title: Kokoro TTS MCP сервер
description: MCP сервер для синтеза речи, использующий Kokoro TTS для генерации MP3 файлов из текста с опциональной автоматической загрузкой в S3 хранилище.
tags:
- AI
- Media
- Storage
- Cloud
- Integration
author: mberg
featured: false
---

MCP сервер для синтеза речи, использующий Kokoro TTS для генерации MP3 файлов из текста с опциональной автоматической загрузкой в S3 хранилище.

## Установка

### UV (Рекомендуется)

```bash
uv run mcp-tts.py
```

### Из исходного кода

```bash
# Clone to a local repo
# Download kokoro-v1.0.onnx and voices-v1.0.bin from https://github.com/thewh1teagle/kokoro-onnx/releases/download/model-files-v1.0/
# Install ffmpeg: brew install ffmpeg (on Mac)
```

## Конфигурация

### Конфигурация MCP

```json
"kokoro-tts-mcp": {
  "command": "uv",
  "args": [
    "--directory",
    "/path/toyourlocal/kokoro-tts-mcp",
    "run",
    "mcp-tts.py"
  ],
  "env": {
    "TTS_VOICE": "af_heart",
    "TTS_SPEED": "1.0",
    "TTS_LANGUAGE": "en-us",
    "AWS_ACCESS_KEY_ID": "",
    "AWS_SECRET_ACCESS_KEY": "",
    "AWS_REGION": "us-east-1",
    "AWS_S3_FOLDER": "mp3",
    "S3_ENABLED": "true",
    "MP3_FOLDER": "/path/to/mp3"
  }
}
```

## Возможности

- Генерация MP3 файлов из текста с использованием Kokoro TTS
- Опциональная автоматическая загрузка в S3 хранилище
- Поддержка множественных голосов и языков
- Настраиваемая скорость речи
- Автоматическая очистка старых MP3 файлов
- Локальное хранение с политиками хранения
- Опция удаления локальных файлов после загрузки в S3
- Конвертация WAV в MP3 с использованием ffmpeg

## Переменные окружения

### Опциональные
- `AWS_ACCESS_KEY_ID` - Ваш AWS access key ID
- `AWS_SECRET_ACCESS_KEY` - Ваш AWS secret access key
- `AWS_S3_BUCKET_NAME` - Имя S3 бакета
- `AWS_S3_REGION` - Регион S3 (например, us-east-1)
- `AWS_S3_FOLDER` - Путь к папке внутри S3 бакета
- `AWS_S3_ENDPOINT_URL` - Опциональный пользовательский endpoint URL для S3-совместимого хранилища
- `MCP_HOST` - Хост для привязки сервера (по умолчанию: 0.0.0.0)
- `MCP_PORT` - Порт для прослушивания (по умолчанию: 9876)

## Примеры использования

```
Convert text to speech: "Hello, world!"
```

```
Read text from a file and convert to MP3
```

```
Generate speech with custom voice and speed settings
```

```
Create MP3 files with automatic S3 upload
```

## Ресурсы

- [GitHub Repository](https://github.com/mberg/kokoro-tts-mcp)

## Примечания

Требует скачивания весов Kokoro ONNX (kokoro-v1.0.onnx и voices-v1.0.bin) и установки ffmpeg для конвертации WAV в MP3. Использует модель Kokoro TTS от Hugging Face. Включает автономный клиент (mcp_client.py) для тестирования TTS запросов.