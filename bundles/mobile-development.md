---
title: Mobile Development
description: Полный стек для мобильной разработки. Flutter, React Native, нативная разработка и публикация в сторах.
category: development
tags:
  - Mobile
  - Flutter
  - iOS
  - Android
  - Apps
featured: false
mcps:
  - filesystem
  - memory
  - sentry
skills:
  - android-viewmodel
  - android-repository-pattern
  - android-unit-test
  - android-retrofit-service
agents:
  - flutter-mobile-app-dev
  - mobile-app-builder
  - app-store-optimizer
  - debugger
prompts: []
---

## Для кого эта связка

Для мобильных разработчиков, создающих приложения для iOS и Android.

## Что включено

### MCP-серверы

**Filesystem** — работа с файлами проекта. Чтение, запись, навигация по структуре.

**Memory** — сохранение контекста проекта между сессиями.

**Sentry** — мониторинг крэшей и ошибок в мобильных приложениях.

### Навыки

**Android ViewModel** — архитектура MVVM для Android.

**Android Repository Pattern** — паттерн репозитория для работы с данными.

**Android Unit Test** — модульное тестирование Android-приложений.

**Android Retrofit Service** — работа с сетью через Retrofit.

### Агенты

**Flutter Mobile App Dev** — разработка кроссплатформенных приложений на Flutter.

**Mobile App Builder** — создание мобильных приложений с нуля.

**App Store Optimizer** — оптимизация для App Store и Google Play.

**Debugger** — отладка и исправление багов.

## Как использовать

1. **Выберите платформу** (Flutter, Native, React Native)
2. **Спроектируйте архитектуру** с Mobile App Builder
3. **Разработайте функционал** с Flutter/Android агентами
4. **Протестируйте** с Unit Test навыком
5. **Оптимизируйте ASO** перед публикацией

### Пример промпта

```
Создай Flutter-виджет для экрана профиля:
- Аватар с возможностью смены фото
- Редактируемые поля: имя, email, телефон
- Кнопка сохранения с валидацией
- Интеграция с BLoC для state management
```

## Архитектура приложения

```
lib/
├── main.dart
├── app/
│   ├── app.dart
│   └── routes.dart
├── core/
│   ├── network/
│   ├── storage/
│   └── utils/
├── features/
│   ├── auth/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   ├── home/
│   └── profile/
└── shared/
    ├── widgets/
    └── theme/
```

## Результат

- Кроссплатформенное приложение
- Чистая архитектура
- Покрытие тестами
- Оптимизированный листинг в сторах
