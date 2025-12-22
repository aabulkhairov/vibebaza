---
title: Anki MCP сервер
description: MCP сервер для Anki — программное управление флеш-карточками, колодами
  и процессом повторения через Model Context Protocol с поддержкой генерации аудио.
tags:
- Productivity
- AI
- Integration
- Storage
- API
author: nietus
featured: false
---

MCP сервер для Anki — программное управление флеш-карточками, колодами и процессом повторения через Model Context Protocol с поддержкой генерации аудио.

## Установка

### NPX

```bash
npx -y github:nietus/anki-mcp
```

### Из исходников

```bash
git clone https://github.com/nietus/anki-mcp
npm install
npm run build
```

### Claude Desktop Bundle

```bash
npm install
npm run build
npm run pack:mcpb
```

## Конфигурация

### Cursor (Windows)

```json
"anki": {
  "command": "cmd",
  "args": [
    "/c",
    "node",
    "c:/Users/YOUR_USERNAME/Downloads/anki-mcp/build/client.js"
  ]
}
```

### Cursor (macOS/Linux)

```json
"anki": {
  "command": "bash",
  "args": [
    "-c",
    "node /Users/YOUR_USERNAME/Downloads/anki-mcp/build/client.js"
  ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `update_cards` | Отметить карточки как отвеченные и обновить их ease после ответа на вопросы |
| `add_card` | Создать новую флеш-карточку в Anki с HTML контентом |
| `add_card_with_audio` | Создать новую флеш-карточку с автоматически сгенерированным аудио через Azure TTS |
| `update_card_with_audio` | Обновить существующую карточку — сгенерировать аудио из поля и добавить в аудио-поле |
| `get_due_cards` | Получить заданное количество карточек для повторения |
| `get_new_cards` | Получить заданное количество новых, ещё не просмотренных карточек |
| `get_deck_names` | Получить список всех названий колод Anki |
| `find_cards` | Найти карточки по сырому поисковому запросу Anki с детальной информацией |
| `update_note_fields` | Обновить конкретные поля существующей заметки Anki |
| `create_deck` | Создать новую колоду Anki |
| `bulk_update_notes` | Массовое обновление полей нескольких заметок за одну операцию |
| `get_model_names` | Список всех доступных типов заметок/моделей Anki |
| `get_model_details` | Получить поля, шаблоны карточек и CSS стили для указанного типа заметок |
| `get_deck_model_info` | Получить информацию о типах заметок, используемых в указанной колоде |
| `add_note_type_field` | Добавить новое поле к типу заметок |

## Возможности

- Программное создание и обновление флеш-карточек
- Управление колодами и типами заметок Anki
- Генерация аудио для флеш-карточек через Azure TTS
- Массовые операции для эффективного управления карточками
- Расширенный поиск и фильтрация карточек
- Поддержка HTML форматирования в карточках
- Мультиязычная генерация аудио
- Интеграция с плагином AnkiConnect

## Переменные окружения

### Опциональные
- `AZURE_API_KEY` — API ключ Azure для генерации text-to-speech аудио
- `ANKI_MEDIA_DIR` — путь к директории медиа Anki (папка collection.media) для хранения аудиофайлов

## Ресурсы

- [GitHub Repository](https://github.com/nietus/anki-mcp)

## Примечания

Требуется Node.js, npm и установленный плагин AnkiConnect, работающий в Anki. Настоятельно рекомендуется локальный запуск, так как AnkiConnect работает только локально. Тестировалось только на Windows. Поддерживает 21+ язык для TTS аудио генерации, включая английский, испанский, французский, немецкий, итальянский, японский, корейский, португальский, русский, китайский, арабский и другие.
