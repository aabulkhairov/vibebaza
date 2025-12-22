---
title: API Development Stack
description: Всё для разработки и документирования API. Проектирование, тестирование, документация и мониторинг.
category: development
tags:
  - API
  - REST
  - GraphQL
  - Documentation
  - Testing
featured: false
mcps:
  - postgres
  - memory
  - sentry
skills:
  - api-design-spec
  - api-authentication
  - api-integration-test
  - api-reference-guide
agents:
  - api-integration-specialist
  - api-tester
  - graphql-architect
  - backend-architect
prompts: []
---

## Для кого эта связка

Для backend-разработчиков и архитекторов, проектирующих и разрабатывающих API.

## Что включено

### MCP-серверы

**PostgreSQL** — работа с базой данных. Запросы, миграции, оптимизация.

**Memory** — сохранение контекста API-дизайна между сессиями.

**Sentry** — мониторинг ошибок и производительности API.

### Навыки

**API Design Spec** — проектирование RESTful и GraphQL API.

**API Authentication** — OAuth2, JWT, API keys и другие методы аутентификации.

**API Integration Test** — написание интеграционных тестов.

**API Reference Guide** — создание документации для разработчиков.

### Агенты

**API Integration Specialist** — интеграция с внешними сервисами.

**API Tester** — тестирование API и поиск уязвимостей.

**GraphQL Architect** — проектирование GraphQL схем.

**Backend Architect** — архитектура backend-систем.

## Как использовать

1. **Спроектируйте API** с API Design Spec
2. **Реализуйте эндпоинты** с помощью Backend Architect
3. **Настройте аутентификацию** с API Authentication
4. **Напишите тесты** с API Tester
5. **Задокументируйте** с API Reference Guide

### Пример промпта

```
Спроектируй REST API для сервиса заказов:

Ресурсы:
- Orders (создание, обновление, отмена)
- Products (каталог, поиск)
- Users (регистрация, профиль)

Требования:
- Пагинация и фильтрация
- Версионирование v1/v2
- Rate limiting
- JWT аутентификация
```

## Структура API

```
api/v1/
├── /auth
│   ├── POST /login
│   ├── POST /register
│   └── POST /refresh
├── /users
│   ├── GET /me
│   └── PATCH /me
├── /products
│   ├── GET /
│   ├── GET /:id
│   └── GET /search
└── /orders
    ├── GET /
    ├── POST /
    ├── GET /:id
    ├── PATCH /:id
    └── DELETE /:id
```

## Результат

- Хорошо спроектированный API
- Полная документация
- Покрытие тестами
- Мониторинг и алертинг
