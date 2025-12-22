---
title: Security & Compliance
description: Инструменты для безопасности и соответствия требованиям. Аудит кода, GDPR, SOC2, пентестинг.
category: security
tags:
  - Security
  - Compliance
  - GDPR
  - SOC2
  - Audit
featured: false
mcps:
  - sentry
  - memory
  - filesystem
skills:
  - bug-bounty-program
  - audit-preparation-guide
  - api-authentication
agents:
  - data-privacy-engineer
  - compliance-automation-specialist
  - legal-compliance-checker
  - code-reviewer
prompts: []
---

## Для кого эта связка

Для специалистов по безопасности, DevSecOps и команд, готовящихся к аудитам SOC2, GDPR.

## Что включено

### MCP-серверы

**Sentry** — мониторинг безопасности и ошибок в production.

**Memory** — хранение контекста аудитов и compliance требований.

**Filesystem** — анализ кода и конфигураций на уязвимости.

### Навыки

**Bug Bounty Program** — организация программы поиска уязвимостей.

**Audit Preparation Guide** — подготовка к SOC2, ISO 27001 аудитам.

**API Authentication** — безопасная аутентификация и авторизация.

### Агенты

**Data Privacy Engineer** — обеспечение соответствия GDPR и privacy.

**Compliance Automation Specialist** — автоматизация compliance процессов.

**Legal Compliance Checker** — проверка юридических требований.

**Code Reviewer** — ревью кода на безопасность.

## Как использовать

1. **Проведите аудит** существующей системы
2. **Определите gaps** в compliance
3. **Создайте план устранения** с Compliance Automation Specialist
4. **Внедрите controls** с Data Privacy Engineer
5. **Подготовьте документацию** для аудиторов

### Пример промпта

```
Создай чеклист для SOC2 Type II аудита:
- Trust Service Criteria: Security, Availability
- Текущая инфраструктура: AWS, PostgreSQL, Rails
- Команда: 15 разработчиков
- Сроки: 3 месяца до аудита
```

## Compliance Framework

```
┌─────────────────────────────────────────────┐
│           COMPLIANCE FRAMEWORK              │
├─────────────────────────────────────────────┤
│                                             │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐     │
│  │  SOC2   │  │  GDPR   │  │ISO 27001│     │
│  └────┬────┘  └────┬────┘  └────┬────┘     │
│       │            │            │           │
│       └────────────┼────────────┘           │
│                    ▼                        │
│  ┌─────────────────────────────────────┐   │
│  │        SECURITY CONTROLS            │   │
│  ├─────────────────────────────────────┤   │
│  │ • Access Management                 │   │
│  │ • Data Encryption                   │   │
│  │ • Logging & Monitoring              │   │
│  │ • Incident Response                 │   │
│  │ • Vendor Management                 │   │
│  └─────────────────────────────────────┘   │
│                                             │
└─────────────────────────────────────────────┘
```

## Результат

- Готовность к аудитам
- Документированные процессы
- Автоматизированный compliance мониторинг
- Защищенная инфраструктура
