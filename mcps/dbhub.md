---
title: DBHub MCP сервер
description: DBHub — это универсальный MCP сервер для баз данных, который предоставляет единый интерфейс для подключения MCP-совместимых клиентов к различным типам баз данных, включая PostgreSQL, MySQL, MariaDB, SQL Server и SQLite, с безопасным доступом и функциями, готовыми к продакшену.
tags:
- Database
- DevOps
- Security
- Integration
- Analytics
author: bytebase
featured: true
---

DBHub — это универсальный MCP сервер для баз данных, который предоставляет единый интерфейс для подключения MCP-совместимых клиентов к различным типам баз данных, включая PostgreSQL, MySQL, MariaDB, SQL Server и SQLite, с безопасным доступом и функциями, готовыми к продакшену.

## Установка

### Docker

```bash
docker run --rm --init \
   --name dbhub \
   --publish 8080:8080 \
   bytebase/dbhub \
   --transport http \
   --port 8080 \
   --dsn "postgres://user:password@localhost:5432/dbname?sslmode=disable"
```

### NPX

```bash
npx @bytebase/dbhub --transport http --port 8080 --dsn "postgres://user:password@localhost:5432/dbname?sslmode=disable"
```

### Демо режим

```bash
npx @bytebase/dbhub --transport http --port 8080 --demo
```

### Из исходников

```bash
pnpm install
pnpm dev
# Для продакшена:
pnpm build
pnpm start --transport stdio --dsn "postgres://user:password@localhost:5432/dbname?sslmode=disable"
```

## Возможности

- Универсальный шлюз: единый интерфейс для PostgreSQL, MySQL, MariaDB, SQL Server и SQLite
- Безопасный доступ: режим только для чтения, SSH туннелирование и поддержка SSL/TLS шифрования
- Мультибазность: одновременное подключение к нескольким базам данных с конфигурацией через TOML
- Готовность к продакшену: ограничение строк, контроль тайм-аутов блокировок и пулинг соединений
- Нативная поддержка MCP: полная реализация Model Context Protocol с ресурсами, инструментами и промптами
- Ресурсы: исследование схем баз данных (схемы, таблицы, индексы, процедуры)
- Инструменты: выполнение SQL с поддержкой транзакций
- Промпты: генерация SQL с помощью ИИ и объяснение баз данных

## Ресурсы

- [GitHub Repository](https://github.com/bytebase/dbhub)

## Примечания

DBHub поддерживает мульти-базовую конфигурацию с использованием TOML файлов, что идеально подходит для управления продакшен, тестовыми и девелоперскими базами данных из одного экземпляра. Полная документация доступна по адресу https://dbhub.ai/. Представлено командой Bytebase — платформы для database DevSecOps с открытым исходным кодом.