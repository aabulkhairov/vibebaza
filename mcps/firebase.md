---
title: Firebase MCP сервер
description: Firebase MCP позволяет AI ассистентам работать напрямую с сервисами Firebase,
  включая Firestore (документная база данных), Storage (управление файлами) и Authentication
  (управление пользователями).
tags:
- Database
- Cloud
- Storage
- API
- Integration
author: gannonh
featured: true
---

Firebase MCP позволяет AI ассистентам работать напрямую с сервисами Firebase, включая Firestore (документная база данных), Storage (управление файлами) и Authentication (управление пользователями).

## Установка

### NPX

```bash
npx -y @gannonh/firebase-mcp
```

### Из исходного кода

```bash
git clone https://github.com/gannonh/firebase-mcp
cd firebase-mcp
npm install
npm run build
```

## Конфигурация

### Конфигурация NPX

```json
{
  "firebase-mcp": {
    "command": "npx",
    "args": [
      "-y",
      "@gannonh/firebase-mcp"
    ],
    "env": {
      "SERVICE_ACCOUNT_KEY_PATH": "/absolute/path/to/serviceAccountKey.json",
      "FIREBASE_STORAGE_BUCKET": "your-project-id.firebasestorage.app"
    }
  }
}
```

### Локальная установка

```json
{
  "firebase-mcp": {
    "command": "node",
    "args": [
      "/absolute/path/to/firebase-mcp/dist/index.js"
    ],
    "env": {
      "SERVICE_ACCOUNT_KEY_PATH": "/absolute/path/to/serviceAccountKey.json",
      "FIREBASE_STORAGE_BUCKET": "your-project-id.firebasestorage.app"
    }
  }
}
```

### HTTP транспорт

```json
{
  "firebase-mcp": {
    "url": "http://localhost:3000/mcp"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `firestore_add_document` | Добавить документ в коллекцию |
| `firestore_list_documents` | Список документов с фильтрацией |
| `firestore_get_document` | Получить конкретный документ |
| `firestore_update_document` | Обновить существующий документ |
| `firestore_delete_document` | Удалить документ |
| `firestore_list_collections` | Список корневых коллекций |
| `firestore_query_collection_group` | Запрос по подколлекциям |
| `storage_list_files` | Список файлов в директории |
| `storage_get_file_info` | Получить метаданные файла и URL |
| `storage_upload` | Загрузить файл из контента |
| `storage_upload_from_url` | Загрузить файл по URL |
| `auth_get_user` | Получить пользователя по ID или email |

## Возможности

- Операции с документной базой данных Firestore
- Управление файлами Firebase Storage с возможностью загрузки
- Управление пользователями и верификация Firebase Authentication
- Поддержка HTTP транспорта для множественных клиентских подключений
- Управление сессиями для HTTP транспорта
- Логирование в файл для отладки
- Работает с Claude Desktop, VS Code, Cursor и Augment Code

## Переменные окружения

### Обязательные
- `SERVICE_ACCOUNT_KEY_PATH` - Путь к JSON файлу с ключом сервисного аккаунта Firebase

### Опциональные
- `FIREBASE_STORAGE_BUCKET` - Имя бакета для Firebase Storage
- `MCP_TRANSPORT` - Тип транспорта (stdio или http)
- `MCP_HTTP_PORT` - Порт для HTTP транспорта
- `MCP_HTTP_HOST` - Хост для HTTP транспорта
- `MCP_HTTP_PATH` - Путь для HTTP транспорта
- `DEBUG_LOG_FILE` - Включить логирование в файл (установить в true или путь к файлу)

## Примеры использования

```
Please test all Firebase MCP tools
```

## Ресурсы

- [GitHub Repository](https://github.com/gannonh/firebase-mcp)

## Примечания

Известная проблема с инструментом firestore_list_collections, показывающим ошибки валидации Zod в логах (не влияет на функциональность). Требует проект Firebase с учетными данными сервисного аккаунта. Поддерживает режимы транспорта stdio и HTTP. HTTP транспорт позволяет множественные клиентские подключения с управлением сессиями.