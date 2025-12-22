---
title: ImageSorcery MCP сервер
description: MCP сервер на основе компьютерного зрения, который предоставляет локальные возможности распознавания и редактирования изображений, включая детекцию объектов, OCR, удаление фона и различные инструменты обработки изображений.
tags:
- AI
- Media
- Productivity
- API
author: Community
featured: false
---

MCP сервер на основе компьютерного зрения, который предоставляет локальные возможности распознавания и редактирования изображений, включая детекцию объектов, OCR, удаление фона и различные инструменты обработки изображений.

## Установка

### pipx (Рекомендуется)

```bash
pipx install imagesorcery-mcp
imagesorcery-mcp --post-install
```

### Ручная настройка виртуального окружения

```bash
python -m venv imagesorcery-mcp
source imagesorcery-mcp/bin/activate
pip install imagesorcery-mcp
imagesorcery-mcp --post-install
```

## Конфигурация

### Установка через pipx

```json
"mcpServers": {
    "imagesorcery-mcp": {
      "command": "imagesorcery-mcp",
      "transportType": "stdio",
      "autoApprove": ["blur", "change_color", "config", "crop", "detect", "draw_arrows", "draw_circles", "draw_lines", "draw_rectangles", "draw_texts", "fill", "find", "get_metainfo", "ocr", "overlay", "resize", "rotate"],
      "timeout": 100
    }
}
```

### Ручная установка venv

```json
"mcpServers": {
    "imagesorcery-mcp": {
      "command": "/full/path/to/venv/bin/imagesorcery-mcp",
      "transportType": "stdio",
      "autoApprove": ["blur", "change_color", "config", "crop", "detect", "draw_arrows", "draw_circles", "draw_lines", "draw_rectangles", "draw_texts", "fill", "find", "get_metainfo", "ocr", "overlay", "resize", "rotate"],
      "timeout": 100
    }
}
```

### HTTP режим

```json
"mcpServers": {
    "imagesorcery-mcp": {
      "url": "http://127.0.0.1:8000/mcp",
      "transportType": "http",
      "autoApprove": ["blur", "change_color", "config", "crop", "detect", "draw_arrows", "draw_circles", "draw_lines", "draw_rectangles", "draw_texts", "fill", "find", "get_metainfo", "ocr", "overlay", "resize", "rotate"],
      "timeout": 100
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `blur` | Размывает указанные прямоугольные или полигональные области изображения с помощью OpenCV |
| `change_color` | Изменяет цветовую палитру изображения |
| `config` | Просмотр и обновление настроек конфигурации ImageSorcery MCP |
| `crop` | Обрезает изображение используя подход с NumPy-срезами OpenCV |
| `detect` | Обнаруживает объекты на изображении с помощью моделей от Ultralytics |
| `draw_arrows` | Рисует стрелки на изображении с помощью OpenCV |
| `draw_circles` | Рисует окружности на изображении с помощью OpenCV |
| `draw_lines` | Рисует линии на изображении с помощью OpenCV |
| `draw_rectangles` | Рисует прямоугольники на изображении с помощью OpenCV |
| `draw_texts` | Рисует текст на изображении с помощью OpenCV |
| `fill` | Заливает указанные области изображения цветом или делает их прозрачными |
| `find` | Находит объекты на изображении по текстовому описанию |
| `get_metainfo` | Получает метаданные файла изображения |
| `ocr` | Выполняет оптическое распознавание символов (OCR) на изображении с помощью EasyOCR |
| `overlay` | Накладывает одно изображение поверх другого с обработкой прозрачности |

## Возможности

- Обрезка, изменение размера и поворот изображений с высокой точностью
- Удаление фона
- Рисование текста и фигур на изображениях
- Добавление логотипов и водяных знаков
- Детекция объектов с использованием современных моделей
- Извлечение текста из изображений с помощью OCR
- Использование широкого спектра предобученных моделей для детекции объектов
- Локальная обработка изображений без отправки на внешние серверы

## Примеры использования

```
copy photos with pets from folder `photos` to folder `pets`
```

```
Find a cat at the photo.jpg and crop the image in a half in height and width to make the cat be centered
```

```
Enumerate form fields on this `form.jpg` with `foduucom/web-form-ui-field-detection` model and fill the `form.md` with a list of described fields
```

```
Blur the area from (150, 100) to (250, 200) with a blur strength of 21 in my image 'test_image.png' and save it as 'output.png'
```

```
Convert my image 'test_image.png' to sepia and save it as 'output.png'
```

## Ресурсы

- [GitHub Repository](https://github.com/sunriseapps/imagesorcery-mcp)

## Примечания

Требует Python 3.10+, ffmpeg, libsm6, libxext6 и системные библиотеки libgl1-mesa-glx. Скрипт пост-установки загружает необходимые модели и устанавливает пакет CLIP. Работает с Claude, Cursor и Cline. Вся обработка выполняется локально без отправки изображений на внешние серверы.