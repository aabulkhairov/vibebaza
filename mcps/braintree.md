---
title: Braintree MCP сервер
description: Неофициальный MCP сервер для взаимодействия с платежными сервисами PayPal Braintree, позволяющий AI системам выполнять платежные операции такие как получение транзакций, создание платежей и управление данными клиентов через GraphQL API.
tags:
- Finance
- API
- Integration
author: QuentinCody
featured: false
---

Неофициальный MCP сервер для взаимодействия с платежными сервисами PayPal Braintree, позволяющий AI системам выполнять платежные операции такие как получение транзакций, создание платежей и управление данными клиентов через GraphQL API.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yourusername/braintree-mcp-server.git
cd braintree-mcp-server
pip install -e .
```

### STDIO транспорт

```bash
python braintree_server.py
```

### SSE транспорт

```bash
python braintree_sse_server.py
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `braintree_ping` | Простой тест подключения для проверки работоспособности ваших Braintree учетных данных |
| `braintree_execute_graphql` | Выполнение произвольных GraphQL запросов к Braintree API |

## Возможности

- Два варианта транспорта: STDIO для интеграции с Claude Desktop и SSE для автономного веб-сервера
- Прямой доступ к возможностям обработки платежей Braintree через GraphQL API
- Управление транзакциями и операции с данными клиентов
- Поддержка множественных клиентских подключений с SSE транспортом
- Поддержка sandbox и production окружений

## Переменные окружения

### Обязательные
- `BRAINTREE_MERCHANT_ID` - Ваш Braintree merchant ID
- `BRAINTREE_PUBLIC_KEY` - Ваш Braintree публичный ключ
- `BRAINTREE_PRIVATE_KEY` - Ваш Braintree приватный ключ
- `BRAINTREE_ENVIRONMENT` - Настройка окружения (sandbox или production)

## Примеры использования

```
Test Braintree connectivity
```

```
Fetch customer payment information and payment methods
```

```
Create a new transaction for a specific amount
```

```
Execute custom GraphQL queries against Braintree API
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/braintree-mcp-server)

## Примечания

Требует Python 3.13+. Учетные данные Braintree должны быть получены из Braintree Control Panel. SSE сервер по умолчанию запускается на 127.0.0.1:8001. MIT License с требованием академического цитирования.