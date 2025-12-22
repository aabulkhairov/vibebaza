---
title: Creatify MCP сервер
description: MCP сервер, который предоставляет доступ к возможностям платформы генерации видео Creatify AI,
  позволяя AI-ассистентам создавать аватар-видео, конвертировать веб-сайты в видео, генерировать
  текст в речь и выполнять AI-редактирование видео через естественный язык.
tags:
- AI
- Media
- API
- Productivity
author: Community
featured: false
---

MCP сервер, который предоставляет доступ к возможностям платформы генерации видео Creatify AI, позволяя AI-ассистентам создавать аватар-видео, конвертировать веб-сайты в видео, генерировать текст в речь и выполнять AI-редактирование видео через естественный язык.

## Установка

### NPM Global

```bash
npm install -g @tsavo/creatify-mcp
```

### Из исходного кода

```bash
git clone https://github.com/TSavo/creatify-mcp.git
cd creatify-mcp
npm install
npm run build
npm link
```

### Автономный сервер

```bash
export CREATIFY_API_ID="your-api-id"
export CREATIFY_API_KEY="your-api-key"
creatify-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "creatify": {
      "command": "creatify-mcp",
      "env": {
        "CREATIFY_API_ID": "your-api-id",
        "CREATIFY_API_KEY": "your-api-key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_avatar_video` | Создание AI аватар-видео с синхронизацией губ |
| `create_url_to_video` | Конвертация веб-сайтов в профессиональные видео |
| `generate_text_to_speech` | Генерация естественно звучащей речи из текста |
| `create_multi_avatar_conversation` | Создание видео с несколькими аватарами в диалоге |
| `create_custom_template_video` | Генерация видео с использованием пользовательских шаблонов |
| `create_ai_edited_video` | Автоматическое редактирование и улучшение видео |
| `create_ai_shorts` | Создание коротких видео (идеально для TikTok, Instagram Reels) |
| `generate_ai_script` | Генерация AI-скриптов для видео |
| `create_custom_avatar` | Проектирование и создание собственных аватаров (DYOA) |
| `manage_music` | Загрузка, управление и использование фоновой музыки |
| `create_advanced_lipsync` | Продвинутая синхронизация губ с контролем эмоций и жестов |
| `how_to_use` | Получение детальной информации об использовании любого инструмента |
| `get_video_status` | Проверка статуса задач генерации видео |

## Возможности

- 12 MCP инструментов, покрывающих 100% функциональности Creatify API
- 6 MCP ресурсов для полного доступа к данным (аватары, голоса, шаблоны, музыка, кредиты)
- 5 готовых workflow для типичных сценариев создания видео
- Отслеживание прогресса в реальном времени во время генерации видео
- AI система самопомощи с инструментом how_to_use
- Продвинутый контроль эмоций и жестов в синхронизации губ
- Создание пользовательских аватаров (DYOA - Design Your Own Avatar)
- AI-генерация скриптов
- Оптимизация коротких видео для социальных сетей
- Управление фоновой музыкой и её интеграция

## Переменные окружения

### Обязательные
- `CREATIFY_API_ID` - Ваш Creatify API ID из настроек аккаунта
- `CREATIFY_API_KEY` - Ваш Creatify API ключ из настроек аккаунта

## Примеры использования

```
Create a professional avatar video with Anna saying 'Welcome to our company!' in 16:9 format
```

```
Make a 30-second TikTok video about coffee brewing tips
```

```
Turn my product landing page into a marketing video
```

```
Generate a script for a 60-second product demo video
```

```
Convert the website https://example.com into a promotional video
```

## Ресурсы

- [GitHub Repository](https://github.com/TSavo/creatify-mcp)

## Примечания

Требует учетные данные Creatify API (план Pro или выше). Построен на основе TypeScript клиентской библиотеки @tsavo/creatify-api-ts. Включает предопределенные шаблоны workflow для типичных сценариев создания видео, таких как демо продуктов, контент для соцсетей, образовательные видео и маркетинговые кампании.