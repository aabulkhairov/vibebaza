---
title: DevOps Pipeline
description: Полный CI/CD стек — от коммита до продакшена. Контейнеризация, оркестрация, мониторинг и алертинг.
category: devops
tags:
  - DevOps
  - CI/CD
  - Docker
  - Kubernetes
  - Monitoring
featured: true
mcps:
  - gitlab
  - cloudflare
  - sentry
  - grafana
skills:
  - python-developer
  - rails-developer
agents:
  - research-agent
  - test-generator
---

## Для кого эта связка

Для DevOps-инженеров, разработчиков и тимлидов, которые хотят построить надежный пайплайн доставки кода.

## Что включено

### MCP-серверы

**GitLab** — Git-репозитории и CI/CD. Пайплайны, код-ревью, управление релизами, container registry.

**Cloudflare** — CDN и защита. DNS, SSL-сертификаты, WAF, Workers для edge computing.

**Sentry** — мониторинг ошибок. Трекинг исключений, performance monitoring, release tracking.

**Grafana** — визуализация метрик. Дашборды, алерты, интеграция с Prometheus и другими источниками.

### Навыки

**Python Developer** — скрипты для автоматизации. CI/CD пайплайны, утилиты для деплоя.

**Rails Developer** — настройка production-окружения. Dockerfile, docker-compose, Procfile.

### Агенты

**Research Agent** — исследование best practices. Анализ конфигураций, поиск оптимальных решений.

**Test Generator** — автоматизация тестирования. Unit-тесты, интеграционные тесты, e2e.

## Как использовать

1. **Настройте GitLab CI/CD** с помощью Claude
2. **Создайте Dockerfile** и docker-compose.yml
3. **Подключите мониторинг** через Sentry и Grafana
4. **Настройте CDN** и защиту через Cloudflare

### Пример промпта

```
Создай CI/CD пайплайн для Rails приложения:
- Стадии: lint, test, build, deploy
- Docker-образы с multi-stage сборкой
- Деплой на production через GitLab CI
- Уведомления в Slack при падении билда
```

## Архитектура пайплайна

```
Commit → Lint → Test → Build → Deploy → Monitor → Alert
   ↓       ↓       ↓       ↓       ↓        ↓        ↓
 GitLab  RuboCop  RSpec  Docker  GitLab  Sentry   Slack
         ESLint  Jest    Image    CI     Grafana
```

## Типичный .gitlab-ci.yml

```yaml
stages:
  - lint
  - test
  - build
  - deploy

lint:
  stage: lint
  script:
    - bundle exec rubocop
    - yarn lint

test:
  stage: test
  script:
    - bundle exec rspec
    - yarn test

build:
  stage: build
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA

deploy:
  stage: deploy
  script:
    - ./deploy.sh
  only:
    - main
```

## Результат

- Автоматический деплой при каждом коммите в main
- Контейнеризированное приложение
- Мониторинг ошибок и производительности
- CDN с защитой от DDoS
