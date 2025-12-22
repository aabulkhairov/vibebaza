---
title: Reed Jobs MCP сервер
description: Model Context Protocol (MCP) сервер, который интегрируется с Reed Jobs API для поиска и получения списков вакансий с Reed.co.uk с расширенными возможностями фильтрации.
tags:
- API
- Search
- Productivity
- Integration
author: kld3v
featured: false
---

Model Context Protocol (MCP) сервер, который интегрируется с Reed Jobs API для поиска и получения списков вакансий с Reed.co.uk с расширенными возможностями фильтрации.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @kld3v/reed_jobs_mcp --client claude
```

### Из исходного кода

```bash
git clone <your-repo-url>
cd reed-jobs-mcp
npm install
# Create .env file with REED_API_KEY
npm run build
npm start
```

## Конфигурация

### Cursor IDE

```json
{
	"mcpServers": {
		"reed-jobs-mcp": {
			"command": "node",
			"args": ["path/to/your/dist/index.js"],
			"cwd": "path/to/your/project"
		}
	}
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `mcp_reed_jobs_search_jobs` | Поиск вакансий с множественными фильтрами включая ключевые слова, местоположение, зарплату, тип контракта и расстояние... |
| `mcp_reed_jobs_get_job_details` | Получение детальной информации по конкретной вакансии используя её ID |

## Возможности

- Поиск вакансий с множественными фильтрами (ключевые слова, местоположение, зарплата, тип контракта)
- Получение детальной информации по вакансиям
- Поддержка фильтра удаленной работы
- Фильтрация по диапазону зарплат
- Поиск по местоположению с параметрами расстояния

## Переменные окружения

### Обязательные
- `REED_API_KEY` - Ваш Reed API ключ с Reed Developer Portal

## Ресурсы

- [GitHub Repository](https://github.com/kld3v/reed_jobs_mcp)

## Примечания

Создан с использованием TypeScript и спроектирован для бесшовной работы с Cursor IDE. Требует Node.js v16 или выше и Reed API ключ с Reed Developer Portal.