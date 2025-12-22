---
title: Mifos X MCP сервер
description: MCP сервер для системы открытого банкинга Mifos X, который позволяет AI агентам получать доступ к финансовым данным и операциям для управления клиентами, кредитами, сбережениями и финансовыми транзакциями.
tags:
- Finance
- API
- Database
- Integration
- CRM
author: Community
featured: false
---

MCP сервер для системы открытого банкинга Mifos X, который позволяет AI агентам получать доступ к финансовым данным и операциям для управления клиентами, кредитами, сбережениями и финансовыми транзакциями.

## Установка

### JBang (Быстрый запуск)

```bash
jbang --quiet org.mifos.community.ai:mcp-server:1.0.0-SNAPSHOT:runner
```

### Нативный исполняемый файл

```bash
./mvnw package -Dnative
./target/mcp-server-1.0.0-SNAPSHOT-runner
```

### Нативная сборка с контейнером

```bash
./mvnw package -Dnative -Dquarkus.native.container-build=true
./target/mcp-server-1.0.0-SNAPSHOT-runner
```

## Возможности

- Совместимость с MCP через транспорты STDIO/SSE
- Конфигурация, независимая от окружения
- Управление клиентами (создание, активация, добавление адресов и персональных референсов)
- Создание и управление кредитными продуктами
- Подача заявки на кредит, одобрение и выдача
- Обработка погашения кредитов
- Создание сберегательных продуктов
- Управление сберегательными счетами (создание, одобрение, активация)
- Операции депозита и снятия средств
- Финансовые операции для экосистемы Mifos X

## Переменные окружения

### Обязательные
- `FINERACT_BASE_URL / MIFOSX_BASE_URL` - Базовый URL вашего экземпляра Fineract
- `FINERACT_BASIC_AUTH_TOKEN / MIFOSX_BASIC_AUTH_TOKEN` - Токен аутентификации API

### Опциональные
- `FINERACT_TENANT_ID / MIFOS_TENANT_ID` - Идентификатор арендатора (по умолчанию: 'default')

## Примеры использования

```
Create the client using first name: OCTAVIO, last name: PAZ, email address: octaviopaz@mifos.org, mobile number: 5518098299 and external id: OCPZ99
```

```
Activate the client OCTAVIO PAZ
```

```
Add the address to the client OCTAVIO PAZ. Fields: address type: HOME, address: PLAZA DE LORETO, neighborhood: DOCTOR ALFONZO, number: NUMBER 10, city: CDMX, country: MÉXICO, postal code: 54440, state province: CDMX
```

```
Create a default loan product named "SILVER" with short name "ST01", principal 10000, 5 repayments, nominal interest rate 10.0%, repayment frequency 2 MONTHS, currency USD
```

```
Apply for an individual loan account for the client OCTAVIO PAZ using loan product SILVER
```

## Ресурсы

- [GitHub Repository](https://github.com/openMF/mcp-mifosx)

## Примечания

Предварительные требования: JDK 21+, Maven. Java реализация использует переменные окружения с префиксом MIFOSX_. Тестируйте с MCP Inspector используя 'npx @modelcontextprotocol/inspector'. Живой чат-бот доступен на https://ai.mifos.community с использованием провайдера Groq.