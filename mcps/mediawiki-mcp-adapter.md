---
title: MediaWiki MCP adapter MCP сервер
description: Адаптер Model Context Protocol, который обеспечивает программное взаимодействие с MediaWiki и WikiBase API для получения и редактирования вики-страниц.
tags:
- API
- Web Scraping
- Integration
- Productivity
author: lucamauri
featured: false
---

Адаптер Model Context Protocol, который обеспечивает программное взаимодействие с MediaWiki и WikiBase API для получения и редактирования вики-страниц.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yourusername/mediawikiadapter.git
cd mediawikiadapter
npm install
npm run build
node build/index.js
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `editPage` | Редактирует страницу MediaWiki с новым содержимым и опциональным резюме |

## Возможности

- Получение содержимого страницы MediaWiki
- Редактирование страницы MediaWiki с новым содержимым и опциональным резюме
- Настраиваемые базовые URL API для различных экземпляров MediaWiki и WikiBase

## Примеры использования

```
Get the content of the Main Page
```

```
Edit a page with updated content and summary
```

## Ресурсы

- [GitHub Repository](https://github.com/lucamauri/MediaWiki-MCP-adapter)

## Примечания

Требует Node.js версии 16 или новее и экземпляр MediaWiki с включенным доступом к API. По умолчанию используются эндпоинты Wikipedia и Wikidata, но могут быть настроены для пользовательских экземпляров. Лицензировано под LGPL-3.0-or-later.