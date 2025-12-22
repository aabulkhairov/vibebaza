---
title: OpenCTI MCP сервер
description: MCP сервер, который обеспечивает бесшовную интеграцию с платформой OpenCTI (Open Cyber Threat Intelligence), позволяя запрашивать и получать данные об угрозах через стандартизированный интерфейс.
tags:
- Security
- API
- Analytics
- Database
- Integration
author: Spathodea-Network
featured: false
install_command: npx -y @smithery/cli install opencti-server --client claude
---

MCP сервер, который обеспечивает бесшовную интеграцию с платформой OpenCTI (Open Cyber Threat Intelligence), позволяя запрашивать и получать данные об угрозах через стандартизированный интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install opencti-server --client claude
```

### Ручная установка

```bash
# Clone the repository
git clone https://github.com/yourusername/opencti-mcp-server.git

# Install dependencies
cd opencti-mcp-server
npm install

# Build the project
npm run build
```

## Конфигурация

### Настройки MCP

```json
{
  "mcpServers": {
    "opencti": {
      "command": "node",
      "args": ["path/to/opencti-server/build/index.js"],
      "env": {
        "OPENCTI_URL": "${OPENCTI_URL}",
        "OPENCTI_TOKEN": "${OPENCTI_TOKEN}"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_latest_reports` | Получает самые свежие отчеты об угрозах |
| `get_report_by_id` | Получает конкретный отчет по его ID |
| `search_malware` | Поиск информации о вредоносном ПО в базе данных OpenCTI |
| `search_indicators` | Поиск индикаторов компрометации |
| `search_threat_actors` | Поиск информации об угрожающих субъектах |
| `get_user_by_id` | Получает информацию о пользователе по ID |
| `list_users` | Выводит список всех пользователей в системе |
| `list_groups` | Выводит список всех групп с их участниками |
| `list_attack_patterns` | Выводит список всех паттернов атак в системе |
| `get_campaign_by_name` | Получает информацию о кампании по названию |
| `list_connectors` | Выводит список всех коннекторов системы |
| `list_status_templates` | Выводит список всех шаблонов статусов |
| `get_file_by_id` | Получает информацию о файле по ID |
| `list_files` | Выводит список всех файлов в системе |
| `list_marking_definitions` | Выводит список всех определений маркировки |

## Возможности

- Получение и поиск данных об угрозах
- Получение последних отчетов и поиск по ID
- Поиск информации о вредоносном ПО
- Запрос индикаторов компрометации
- Поиск угрожающих субъектов
- Управление пользователями и группами
- Список всех пользователей и групп
- Получение детальной информации о пользователе по ID
- Операции с объектами STIX
- Список паттернов атак

## Переменные окружения

### Обязательные
- `OPENCTI_URL` - URL вашего экземпляра OpenCTI
- `OPENCTI_TOKEN` - Ваш токен API OpenCTI

## Ресурсы

- [GitHub Repository](https://github.com/Spathodea-Network/opencti-mcp)

## Примечания

Требует Node.js версии 16 или выше и доступ к экземпляру OpenCTI с токеном API. Примечания по безопасности включают в себя: никогда не коммитьте файл .env или токены API в систему контроля версий и держите учетные данные OpenCTI в безопасности.