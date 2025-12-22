---
title: Salesforce MCP (AiondaDotCom) MCP сервер
description: MCP сервер, который обеспечивает бесшовную интеграцию с Salesforce через OAuth аутентификацию, позволяя AI ассистентам взаимодействовать с любой Salesforce организацией через безопасный универсальный интерфейс с возможностями умного обучения.
tags:
- CRM
- API
- Integration
- Productivity
- Database
author: AiondaDotCom
featured: false
---

MCP сервер, который обеспечивает бесшовную интеграцию с Salesforce через OAuth аутентификацию, позволяя AI ассистентам взаимодействовать с любой Salesforce организацией через безопасный универсальный интерфейс с возможностями умного обучения.

## Установка

### NPX (Рекомендуется)

```bash
npx @aiondadotcom/mcp-salesforce
```

### Из исходников

```bash
git clone https://github.com/AiondaDotCom/mcp-salesforce.git
cd mcp-salesforce
npm install
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "salesforce": {
      "command": "npx",
      "args": ["@aiondadotcom/mcp-salesforce"]
    }
  }
}
```

### Claude Desktop (Локально)

```json
{
  "mcpServers": {
    "salesforce": {
      "command": "node",
      "args": ["/path/to/mcp-salesforce/src/index.js"]
    }
  }
}
```

### VS Code MCP

```json
{
  "servers": {
    "salesforce": {
      "command": "npx",
      "args": ["@aiondadotcom/mcp-salesforce"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `salesforce_learn` | Изучает вашу полную установку Salesforce - анализирует все объекты, поля и кастомизации... |
| `salesforce_installation_info` | Показывает обзор изученной установки Salesforce включая доступные объекты, кастомные поля... |
| `salesforce_query` | Выполняет SOQL запросы к любому объекту Salesforce |
| `salesforce_create` | Создаёт новые записи в любом объекте Salesforce |
| `salesforce_update` | Обновляет существующие записи в Salesforce |
| `salesforce_delete` | Удаляет записи из Salesforce (необратимое действие) |
| `salesforce_describe` | Получает информацию о схеме для объектов и полей |
| `salesforce_backup` | Создаёт комплексные бэкапы всех данных и файлов Salesforce с детальной информацией для восстановления |
| `salesforce_backup_list` | Показывает доступные бэкапы со статистикой и метаданными |
| `salesforce_time_machine` | Анализирует изменения данных между разными временными точками бэкапов и позволяет точечное восстановление |
| `salesforce_auth` | Аутентификация с Salesforce через OAuth поток, автоматически определяет когда нужна аутентификация |

## Возможности

- Бесшовная OAuth аутентификация с автоматическим обновлением токенов
- Нулевая ручная настройка - Claude обрабатывает аутентификацию прозрачно
- Универсальная интеграция с Salesforce для любой организации включая кастомные объекты
- Умное изучение установки которое анализирует полную настройку Salesforce
- Динамическое обнаружение схемы которое адаптируется к вашей конфигурации
- Полные CRUD операции для любых записей Salesforce
- Комплексная система бэкапов с восстановлением на определённый момент времени
- Функция Time Machine для анализа исторических данных
- Поддержка множества форматов файлов для ContentVersions, Attachments и Documents
- Кроссплатформенное хранение учётных данных в домашней директории пользователя

## Примеры использования

```
Получить недавние контакты за этот месяц
```

```
Создать новый контакт с именем и email
```

```
Обновить email адрес контакта
```

```
Изучить мою полную установку Salesforce
```

```
Показать какие кастомные объекты доступны в моей организации
```

## Ресурсы

- [GitHub Repository](https://github.com/AiondaDotCom/mcp-salesforce)

## Примечания

Требует Node.js 18+ и Salesforce Connected App с настроенным OAuth. Учётные данные безопасно хранятся в ~/.mcp-salesforce.json с кэшем в ~/.mcp-salesforce-cache/. Сервер автоматически обрабатывает настройку через интерфейс Claude - никаких ручных команд в терминале не требуется.