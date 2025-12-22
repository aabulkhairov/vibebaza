---
title: AWS Cloud Stack
description: Полный набор инструментов для работы с AWS. Управление ресурсами, S3, Lambda, мониторинг и оптимизация затрат.
category: devops
tags:
  - AWS
  - Cloud
  - Infrastructure
  - DevOps
  - S3
featured: true
mcps:
  - aws
  - aws-s3
  - aws-cost-explorer
  - cloudflare
skills:
  - python-developer
  - rails-developer
agents:
  - cloud-architect
  - devops-automator
  - infrastructure-maintainer
prompts: []
---

## Для кого эта связка

Для DevOps-инженеров, архитекторов и разработчиков, работающих с AWS инфраструктурой.

## Что включено

### MCP-серверы

**AWS** — полный доступ к AWS сервисам. EC2, Lambda, DynamoDB, SQS и другие.

**AWS S3** — работа с объектным хранилищем. Загрузка, скачивание, управление бакетами.

**AWS Cost Explorer** — анализ и оптимизация затрат на облако.

**Cloudflare** — CDN и защита. Кэширование, DDoS-защита, DNS.

### Навыки

**Python Developer** — автоматизация AWS с Boto3.

**Rails Developer** — интеграция Rails приложений с AWS.

### Агенты

**Cloud Architect** — проектирование облачной архитектуры.

**DevOps Automator** — автоматизация развертывания и мониторинга.

**Infrastructure Maintainer** — поддержка и обновление инфраструктуры.

## Как использовать

1. **Подключите AWS credentials** через MCP
2. **Спроектируйте архитектуру** с Cloud Architect
3. **Автоматизируйте деплой** с DevOps Automator
4. **Оптимизируйте затраты** с Cost Explorer

### Пример промпта

```
Создай Terraform конфигурацию для:
- VPC с публичными и приватными подсетями
- ALB для балансировки нагрузки
- Auto Scaling Group с EC2 инстансами
- RDS PostgreSQL в приватной подсети
```

## Архитектура

```
                    ┌─────────────┐
                    │ CloudFlare  │
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │     ALB     │
                    └──────┬──────┘
              ┌────────────┼────────────┐
              │            │            │
        ┌─────▼─────┐┌─────▼─────┐┌─────▼─────┐
        │   EC2    ││   EC2    ││   EC2    │
        └─────┬─────┘└─────┬─────┘└─────┬─────┘
              └────────────┼────────────┘
                    ┌──────▼──────┐
                    │   RDS/S3   │
                    └─────────────┘
```

## Результат

- Масштабируемая облачная инфраструктура
- Автоматизированные деплои
- Оптимизированные затраты
- Мониторинг и алертинг
