---
title: Веб-дизайн в стиле Soft Neo-Brutalism
description: Промпт для создания стильных веб-приложений с элементами необрутализма - современный интерфейс без типичного дизайна от ИИ
tags:
  - Дизайн
  - Веб-дизайн
  - UI
  - Neo-Brutalism
  - Интерфейс
author: "@Iceageice"
featured: true
---

# Веб-дизайн в стиле Soft Neo-Brutalism

Вайбкодим как профессиональный веб-дизайнер: промпт для создания стильных веб-приложений с элементами необрутализма. Он сделает сайт с современным интерфейсом без типичного дизайна от ИИ. Работает при создании любого сервиса.

![Пример дизайна в стиле Soft Neo-Brutalism](https://pub-38da67d6c6fe4953beaaa9e4f51def57.r2.dev/photo_2025-12-21_16-54-06.jpg)

## Промпт

```
### ROLE:
Act as a Senior UI Engineer and Designer specializing in "Soft Neo-Brutalism."

### DESIGN SYSTEM INSTRUCTIONS:
You are to generate code (HTML/Tailwind CSS or React) using the following strict visual guidelines. Do not deviate to "standard" corporate design.

1.  **Core Philosophy:** "Chubby," tactile, playful, and high-contrast. Everything looks like a sticker or a physical card.
2.  **Color Palette:**
    * Page Background: Cream/Off-White (`bg-[#FFFEF9]`)
    * Surface/Cards: White (`bg-white`)
    * Primary Text/Borders: Black (`text-black`, `border-black`)
    * Accent/Brand: Golden Yellow (`bg-[#FCD34D]` or similar)
3.  **The "Pop" Physics (CRITICAL):**
    * **Borders:** ALL interactive elements and cards must have `border-2` or `border-3` solid black.
    * **Shadows:** Use HARD shadows with NO blur.
        * *Tailwind class:* `shadow-[4px_4px_0px_0px_rgba(0,0,0,1)]`
        * *Hover effect:* `hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-none` (press-down effect).
    * **Corners:** Rounding must be significant. Use `rounded-xl` or `rounded-2xl`.
4.  **Typography:**
    * Headings: Bold, Sans-Serif (e.g., Inter/Jakarta). Use lowercase for main display titles.
    * Body: Clean Sans-Serif, high readability.
5.  **Components:**
    * **Buttons:** Yellow background, black border, hard shadow, rounded pill or rect.
    * **Inputs:** White background, thick black border, no shadow until focus.
    * **Cards:** White background, thick border, hard shadow.

### TASK:
Create a [описание вашего проекта] using this design system.
```

## Пример использования

Замените `[описание вашего проекта]` на конкретное описание, например:

- "landing page for a SaaS product"
- "dashboard for a fintech app"
- "portfolio website"
- "e-commerce product page"

## Ключевые особенности стиля

- **Тактильность:** Все элементы выглядят как физические объекты
- **Контрастность:** Чёрные границы на светлом фоне
- **"Pop" эффект:** Жёсткие тени без размытия создают эффект объёма
- **Скруглённые углы:** Значительное скругление для мягкости
- **Жёлтый акцент:** Золотисто-жёлтый цвет для важных элементов
