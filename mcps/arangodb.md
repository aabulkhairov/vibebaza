---
title: ArangoDB MCP сервер
description: TypeScript-based MCP сервер, который обеспечивает возможности взаимодействия с базой данных через ArangoDB, реализуя основные операции с базой данных для бесшовной интеграции с ArangoDB через MCP инструменты.
tags:
- Database
- Integration
- DevOps
- Storage
- Analytics
author: Community
featured: false
---

TypeScript-based MCP сервер, который обеспечивает возможности взаимодействия с базой данных через ArangoDB, реализуя основные операции с базой данных для бесшовной интеграции с ArangoDB через MCP инструменты.

## Установка

### NPM Global

```bash
npm install -g arango-server
```

### NPX

```bash
npx arango-server
```

### Smithery

```bash
npx -y @smithery/cli install @ravenwits/mcp-server-arangodb --client claude
```

## Конфигурация

### VSCode MCP Конфигурация

```json
{
	"servers": {
		"arango-mcp": {
			"type": "stdio",
			"command": "npx",
			"args": ["arango-server"],
			"env": {
				"ARANGO_URL": "http://localhost:8529",
				"ARANGO_DB": "v20",
				"ARANGO_USERNAME": "app",
				"ARANGO_PASSWORD": "75Sab@MYa3Dj8Fc"
			}
		}
	}
}
```

### Claude Desktop / Cline

```json
{
	"mcpServers": {
		"arango": {
			"command": "node",
			"args": ["/path/to/arango-server/build/index.js"],
			"env": {
				"ARANGO_URL": "your_database_url",
				"ARANGO_DB": "your_database_name",
				"ARANGO_USERNAME": "your_username",
				"ARANGO_PASSWORD": "your_password"
			}
		}
	}
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `arango_query` | Выполнение AQL запросов с опциональными переменными привязки для параметризованных запросов |
| `arango_insert` | Вставка документов в коллекции с автоматической генерацией ключей, если не предоставлены |
| `arango_update` | Обновление существующих документов по имени коллекции и ключу документа |
| `arango_remove` | Удаление документов из коллекций по имени коллекции и ключу документа |
| `arango_backup` | Резервное копирование всех коллекций в JSON файлы для бэкапа данных и целей миграции |
| `arango_list_collections` | Список всех коллекций в базе данных с именами, ID и типами |
| `arango_create_collection` | Создание новой коллекции с настраиваемым типом и поведением waitForSync |

## Возможности

- Выполнение AQL запросов с поддержкой переменных привязки
- Вставка, обновление и удаление документов из коллекций
- Резервное копирование коллекций в JSON файлы
- Список и создание коллекций базы данных
- Автоматическая генерация ключей документов
- Поддержка как документных, так и граничных коллекций
- Дизайн, агностичный к структуре базы данных

## Переменные окружения

### Обязательные
- `ARANGO_URL` - URL сервера ArangoDB (порт по умолчанию 8529 для локальной разработки)
- `ARANGO_DB` - Имя базы данных
- `ARANGO_USERNAME` - Пользователь базы данных
- `ARANGO_PASSWORD` - Пароль базы данных

## Примеры использования

```
List all collections in the database
```

```
Query all users
```

```
Insert a new document with name 'John Doe' and email 'john@example.com' to the 'users' collection
```

```
Update the document with key '123456' or name 'Jane Doe' to change the age to 48
```

```
Create a new collection named 'products'
```

## Ресурсы

- [GitHub Repository](https://github.com/ravenwits/mcp-server-arangodb)

## Примечания

Предназначен только для использования в разработке - не рекомендуется для продакшн баз данных из-за рисков безопасности. Совместим с приложением Claude Desktop и расширениями VSCode, такими как Cline. Требует VSCode 1.99.0+ для интеграции с агентом VSCode. Поддерживает MCP Inspector для отладки.