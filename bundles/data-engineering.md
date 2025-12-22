---
title: Data Engineering
description: Полный стек для построения data pipelines. ETL, хранилища данных, оркестрация и качество данных.
category: analytics
tags:
  - Data
  - ETL
  - Pipeline
  - Analytics
  - BigData
featured: true
mcps:
  - postgres
  - clickhouse
  - sqlite
  - airflow
skills:
  - airflow-dag-builder
  - change-data-capture
  - bigquery-partitioning
agents:
  - data-engineer
  - database-optimizer
  - analytics-reporter
prompts: []
---

## Для кого эта связка

Для дата-инженеров и аналитиков, строящих пайплайны обработки данных.

## Что включено

### MCP-серверы

**PostgreSQL** — OLTP база данных. Транзакции, источник данных.

**ClickHouse** — OLAP база для аналитики. Быстрые агрегации на больших данных.

**SQLite** — легковесная база для локальной разработки и тестирования.

**Airflow** — оркестрация пайплайнов. DAG, расписание, мониторинг.

### Навыки

**Airflow DAG Builder** — создание DAG для оркестрации задач.

**Change Data Capture** — захват изменений из источников.

**BigQuery Partitioning** — оптимизация партиционирования таблиц.

### Агенты

**Data Engineer** — построение надежных data pipelines.

**Database Optimizer** — оптимизация запросов и схем.

**Analytics Reporter** — создание аналитических отчетов.

## Как использовать

1. **Определите источники** данных
2. **Создайте DAG** для ETL процессов
3. **Настройте CDC** для инкрементальной загрузки
4. **Оптимизируйте запросы** с Database Optimizer

### Пример промпта

```
Создай Airflow DAG для ETL пайплайна:
- Источник: PostgreSQL (orders, products, users)
- Приемник: ClickHouse (data warehouse)
- Расписание: каждый час
- Логика: инкрементальная загрузка по updated_at
- Алерты: Slack при ошибках
```

## Архитектура Data Pipeline

```
┌────────────┐     ┌────────────┐     ┌────────────┐
│ PostgreSQL │     │   MySQL    │     │    API     │
│   (OLTP)   │     │   (OLTP)   │     │  Sources   │
└─────┬──────┘     └─────┬──────┘     └─────┬──────┘
      │                  │                  │
      └──────────────────┼──────────────────┘
                         │
                  ┌──────▼──────┐
                  │   Airflow   │
                  │  (Extract)  │
                  └──────┬──────┘
                         │
                  ┌──────▼──────┐
                  │  Transform  │
                  │   (dbt)     │
                  └──────┬──────┘
                         │
                  ┌──────▼──────┐
                  │ ClickHouse  │
                  │   (OLAP)    │
                  └──────┬──────┘
                         │
                  ┌──────▼──────┐
                  │  Dashboards │
                  │  (Metabase) │
                  └─────────────┘
```

## Результат

- Надежные data pipelines
- Real-time аналитика
- Оптимизированные запросы
- Мониторинг качества данных
