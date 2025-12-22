---
title: FPE Demo MCP сервер
description: Легковесный MCP сервер, демонстрирующий FF3 форматосохраняющее шифрование для безопасной защиты данных в LLM workflow, с настраиваемыми режимами аутентификации и поддержкой stdio и HTTP транспортов.
tags:
- Security
- API
- Integration
- Productivity
author: Horizon-Digital-Engineering
featured: false
---

Легковесный MCP сервер, демонстрирующий FF3 форматосохраняющее шифрование для безопасной защиты данных в LLM workflow, с настраиваемыми режимами аутентификации и поддержкой stdio и HTTP транспортов.

## Установка

### Из исходного кода

```bash
npm install
npm run build
npm start
```

### HTTP сервер

```bash
npm run start:http
```

### HTTP сервер с CORS

```bash
CORS_ORIGIN=https://playground.ai.cloudflare.com npm run start:http
```

### Деплой на DigitalOcean

```bash
https://cloud.digitalocean.com/apps/new?repo=https://github.com/Horizon-Digital-Engineering/fpe-demo-mcp/tree/main
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `fpe_encrypt` | Шифрует строку из цифр и возвращает результат с префиксом ENC_FPE: |
| `fpe_decrypt` | Расшифровывает ранее зашифрованные данные с префиксом ENC_FPE: |

## Возможности

- FF3 FPE для цифр (radix-10)
- Несколько режимов аутентификации: authless, debug, test, production
- Префикс ENC_FPE: для видимости зашифрованных значений
- Поддержка stdio (локально) и HTTP (веб) транспортов
- Аутентификация через общий секрет или JWT
- Поддержка CORS для браузерного тестирования
- Нормализация входных данных к цифрам перед шифрованием

## Переменные окружения

### Опциональные
- `AUTH_MODE` - Режим аутентификации: authless (по умолчанию), debug, test или production
- `AUTH_TOKEN` - Общий секрет для аутентификации в test режиме
- `AUTH_JWT_SECRET` - Ключ подписи JWT (по умолчанию demo-secret)
- `AUTH_JWT_ISS` - Валидация издателя JWT
- `AUTH_JWT_AUD` - Валидация аудитории JWT
- `FPE_KEY` - 32-символьный hex ключ для FPE шифрования
- `FPE_TWEAK` - 14-символьный hex tweak для FPE шифрования
- `CORS_ORIGIN` - CORS origin для браузерного тестирования

## Примеры использования

```
Encrypt a SSN like 123-45-6789
```

```
Decrypt an encrypted value with ENC_FPE: prefix
```

```
Demonstrate format-preserving encryption for sensitive data
```

```
Test authentication patterns with shared secrets or JWTs
```

## Ресурсы

- [GitHub Repository](https://github.com/Horizon-Digital-Engineering/fpe-demo-mcp)

## Примечания

Это демо-реализация для изучения концепций FF3 FPE и MCP аутентификации. Для продакшн использования реализуйте правильное управление ключами, индивидуальные tweaks для каждой записи, журналы аудита и функции соответствия нормативам. Сервер работает на http://127.0.0.1:8765/mcp для HTTP транспорта. Формат удаленного MCP URL: https://<your-app>.ondigitalocean.app/mcp